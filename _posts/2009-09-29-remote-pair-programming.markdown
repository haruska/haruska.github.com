---
layout: post
title: Remote Pair Programming with Screen and Vim
---

There have been quite a few blog posts around the ruby community on [pair programming](http://www.extremeprogramming.org/rules/pair.html). [Obie Fernandez thinks it isn't for every programmer](http://blog.obiefernandez.com/content/2009/09/10-reasons-pair-programming-is-not-for-the-masses.html)  while [Josh Susser thinks it isn't right for every project](http://blog.hasmanythrough.com/2009/9/23/pair-programming-isnt-right-for-all-projects). I tend to agree with Josh and disagree with Obie. Obie has writing style that seems to make the assumption that his company's methods aren't just the best but the gold standard. In this case he does have a good method for pair programming. However, it isn't the only nor the best method. The best is whatever works for your situation given the programmer you're working with. 

It isn't an [extreme programming](http://www.extremeprogramming.org) requirement that you're running on Mac. If you're deploying on Linux and you're using Ruby on Rails and vim for your development then logically Linux would be the best OS choice on which to develop. If you're still sold on TextMate, I'd recommend trying emacs but it is your choice. In that case, you have to compromise your development OS choice and go with Mac.

Everyone I happen to pair program with can use vim. Some of us use Mac others Linux. We also enjoy the flexibility of either going in to the office or working remotely we've tried a couple of different solutions for remote pair programming:

* iChat screen share
** Easiest network setup
** OS X only
** Bandwidth hog (need large pipe on both ends)
** Sends raw keyboard signals (dvorak/querty pairs hard)

* Skype screen share
** Easiest network setup
** Beta OS Support (OS X and Windows only ATM)
** Bandwidth hog

* VNC and Skype
** Platform agnostic
** VNC requires NAT traversal
** Bandwidth heavy (less than iChat)

* SSH, Screen and Skype
** Platform agnostic
** Very low bandwidth usage
** Familiar terminal environment
** GUI text editors not supported
** may require NAT traversal

We started by trying screen sharing software. This works pretty well with large bandwidth pipes on both ends. Sometimes the screen repainting can be enough of a delay to break co-understanding. This is especially true when using vim navigation. All screen sharing (iChat, Skype, VNC) seemed to have this issue.

We found that all we were really trying to share was the text editor. With some [helpful tips from Linux.com](http://www.linux.com/archive/feature/56443), we were able to get screen with a shared session working. This can be done on any machine where both developers have SSH access. In the following example, John and Pete ssh into a common machine and share a terminal screen session.

*User john:*

	ssh john@common-machine
	screen -S pairprog
	Ctrl-a :multiuser on
	Ctrl-a :acladd pete

*User pete:*

	ssh pete@common-machine
	screen -X john/pairprog

We found it as responsive as any other remote terminal and had the added benefit of not dedicating the developers' laptops to the task. This is useful for when you're researching how to solve a problem or looking up API documentation while pairing. Our team found this method of pair programming so useful, we considered it even when in the office. It allows developers to stay in their environments they're comfortable with and get real work done.

I hope Obie's post won't discourage "the masses" from pair programming. Figure out what works for you and make it happen. Pair programming has lots of benefits both to the code base and the participating developers. Similar to TDD, it doesn't just happen overnight. Pair Programming is a skill that developers need to constantly get better at to succeed.
