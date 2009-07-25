--- 
layout: post
typo_id: 22
title: eager loading polymorphic associations in rails
---
**Update: now wrapped into the [polymorphic_include plugin](http://github.com/haruska/polymorphic_include)**. The code below has some memory leaks in the eval sections.

Polymorphic associations in Ruby on Rails seem like a good idea until it comes time to join the tables back together. Since it is impossible to eager load the data with a :include parameter, we're doing the next best thing.

We have **Content** objects that have two polymorphic associations (content type and source). When trying to show search results you actually need all of the data which means it is two additional queries per tuple. Instead, we reduced it to **k** queries per page where k is the number of different types of objects.

Enough chatting, here's the code for overriding the **Content.find** method. It assumes you are using the default "_type" suffix. With this code you can just use a :include directive in your finds and it will return your associations instead of throwing an exception.

    def self.find(*args)
      options = args.last.is_a?(Hash) ? args.last : {}
      poly_includes = {}
      # Try the regular find, if it throws the polymorph error, then we need to do extra processing
      begin
        res = super
      rescue ActiveRecord::EagerLoadPolymorphicError => e
        # remove the polymorph :includes and retry regular find
        sym = eval(e.message.split.last)
        inc = options[:include]
        logger.debug { "Content polymorph find triggered on: #{sym}, #{inc.inspect}" }
        # we preserve any sub_includes for the polymorph for use when doing the
        # polymorph find.  This doesn't support recursive polymorph structures
        poly_sub_includes = nil
        if inc.is_a?(Array)
          if inc.first.is_a?(Hash)
            poly_sub_includes = inc.first.delete(sym)
          else
            poly_sub_includes = inc.delete(sym)
          end
        else
          options.delete(:include)
        end
        logger.debug { "Content polymorph sub_includes: #{poly_sub_includes.inspect}" }
        poly_includes[sym] = poly_sub_includes
        if inc.blank? || inc.first.blank?
          options.delete(:include)
        end
        retry
      end
      # for each polymorph include we removed in rescue above, query that
      # poymorph's table using the ids for the polymorph that were fetched
      # in the parent object from normal find
      poly_includes.each do |sym, sub_includes|
        if res.respond_to? :group_by
          res.group_by {|r| eval "r.#{sym.to_s}_type"}.each do |stype, set|
            begin
              stype_class = eval stype
              id_sym = "#{sym.to_s}_id".to_sym
              ids = set.collect(&id_sym)
              sources = stype_class.find(ids, :include => sub_includes)
              sources = [sources] unless sources.is_a? Array
              sources_map = {}
              sources.each {|s| sources_map[s.id] = s}
              set.each { |c| c.send("#{sym.to_s}=", sources_map[c.attributes[id_sym.to_s]]) }
            rescue ActiveRecord::ConfigurationError => e
              # If the polymoprh sub_inlcude is for an association that is not for this
              # polymorph, remove it and try again
              assoc = e.message.match(/Association named '([^']+)'/).to_a[1]
              if assoc
                logger.debug { "Content polymorph wrong assoc for polymorph: #{assoc}, #{sub_includes.inspect}" }
                assoc = assoc.to_sym
                if sub_includes == assoc
                  sub_includes = nil
                elsif sub_includes.is_a? Array
                  sub_includes.delete_if { |k, v| k == assoc}
                elsif sub_includes.is_a? Hash
                  sub_includes.delete assoc
                end
                retry
              else
                raise
              end
            end
          end
        else
          eval "res.#{sym.to_s}"
        end
      end
      return res
    end
