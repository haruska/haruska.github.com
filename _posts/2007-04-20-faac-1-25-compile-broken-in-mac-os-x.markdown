--- 
layout: post
typo_id: 16
title: FAAC 1.25 compile broken in Mac OS X
---
Ran in to this the other day. The bootstrap script and the config.status file that's created on ./configure contains dos ^M chars which cause the bootstrap and config to fail before building. A quick workaround:

    dos2unix bootstrap
    ./bootstrap
    ./configure #this will fail
    dos2unix config.status
    ./config.status
    make
    sudo make install

I'm guessing someone with check-in access to the source runs a windows machine?

**Update:** it is actually just easier to install the MacPorts version then my steps above. Don't know why I didn't check the repository first!

**Update2:** the MacPorts version actually doesn't include the mp4 encoding options?!? Stick with compiling it yourself.
