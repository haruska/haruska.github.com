--- 
layout: post
typo_id: 25
title: installing mysql gem on os x 10.5
---
I was upgrading my machine to Rails 2.0.1 and ran into this snag. If you have mysql installed on OS X and are trying to install the mysql gem, I guess it points to the wrong installation directory for mysql. I got around it with the following gem command:

    sudo gem install mysql -- --with-mysql-config=/usr/local/mysql/bin/mysql_config

Without the build flags, you get this error:

    $ sudo gem install mysql
    Building native extensions. This could take a while...
    ERROR: Error installing mysql:
    ERROR: Failed to build gem native extension.

    /usr/local/bin/ruby extconf.rb install mysql --include-dependencies
    checking for mysql_query() in -lmysqlclient... no
    checking for main() in -lm... yes
    checking for mysql_query() in -lmysqlclient... no
    checking for main() in -lz... yes
    checking for mysql_query() in -lmysqlclient... no
    checking for main() in -lsocket... no
    checking for mysql_query() in -lmysqlclient... no
    checking for main() in -lnsl... no
    checking for mysql_query() in -lmysqlclient... no
    *** extconf.rb failed ***
