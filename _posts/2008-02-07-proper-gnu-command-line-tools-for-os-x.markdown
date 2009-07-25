--- 
layout: post
typo_id: 30
title: proper GNU command line tools for OS X
---
best advice for linux to mac switchers: install [macports](http://www.macports.org/), then execute the following two commands to get proper GNU command line utilities:

    sudo port -c install coreutils +with_default_names
    sudo port -c install findutils +with_default_names
