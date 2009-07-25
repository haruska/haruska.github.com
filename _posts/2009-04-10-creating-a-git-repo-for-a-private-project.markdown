--- 
layout: post
typo_id: 47
title: Creating a git repo for a private project
---
I seem to be doing this more frequently whenever hacking on a new project. It's easy to set up a master repo on a remote server that you have ssh access to, I just always forget the commands. Here they are for reference:

Create a new local repo:

    mkdir myproject
    cd myproject
    git init
    touch README
    git add .
    git commit -m"first checkin"
    cd ..


Create a bare tree

    git clone --bare myproject myproject.git
    touch myproject.git/git-daemon-export-ok


Upload to remote machine (in this case a "/src" folder already on the server)

    scp -r myproject.git server.domain.com:/src/


Check back out from remote repo

    rm -rf myproject
    git clone server.domain.com:/src/myproject.git


You should be all set. Your "master" is now on your remote server. You can branch, push, pull, etc the same as you would on github or similar.
