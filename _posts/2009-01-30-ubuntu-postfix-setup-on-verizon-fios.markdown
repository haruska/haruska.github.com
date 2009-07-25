--- 
layout: post
typo_id: 45
title: ubuntu postfix setup on verizon fios
---
It took me more googling than it should have to figure out how to setup a home server to relay email through verizon's smtp server. Here's what I did.

First, you need a fully qualified domain name (FQDN). This can be set in ubuntu by:

    sudo /bin/hostname myserver.domain.com

Next, install postfix and mailutils:

    sudo apt-get install postfix mailutils

Set up your /etc/postfix/main.cf. Here's what mine looks like:

    smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
    biff = no

    # appending .domain is the MUA's job.
    append_dot_mydomain = no

    readme_directory = no

    # TLS parameters
    smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
    smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
    smtpd_use_tls=yes
    smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
    smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

    # See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
    # information on enabling SSL in the smtp client.

    myhostname = myserver.domain.com
    alias_maps = hash:/etc/aliases
    alias_database = hash:/etc/aliases
    myorigin = /etc/mailname
    mydestination = myserver.domain.com, myserver, localhost.localdomain, localhost

    relayhost = [outgoing.verizon.net]
    smtp_connection_cache_destinations = outgoing.verizon.net
    smtp_sasl_auth_enable = yes
    smtp_sasl_password_maps = static:username@verizon.net:password
    smtp_sasl_security_options = noanonymous
    default_destination_concurrency_limit = 4
    soft_bounce = yes

    mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
    mailbox_command = procmail -a "$EXTENSION"
    mailbox_size_limit = 0
    recipient_delimiter = +
    inet_interfaces = all

restart postfix and you should be all set

    /etc/init.d/postfix restart

to test from the command line, use mail

    myserver> mail email@isp.com
    Cc:
    Subject: Testing postfix
    test
    ^D
