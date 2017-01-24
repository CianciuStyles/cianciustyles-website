---
title: My First Contribution To Open Source!
date: 2017-01-23 21:37:06
tags:
	- Python
	- Django
	- Open Source
---
Hello again!

Since I started my new job last June, I have been fulfilling one of my long-standing desires: to learn everything I could about the [Django][1] framework. Unsurprisingly, this craving has been postponed many times by several factors, but now that I am getting my hands dirty with it every single day, I can really acknowledge the admiration and regard you can easily read about it all over the Internet, and I must say I agree with it (except in some rather peculiar circumstances :P)!

Anyway, to understand better what's going on and why things work in a certain way (and why some others don't), I thought it would be a good idea to find some Django projects on [GitHub][2], read their code to see how they organized it, and maybe apply some of the knowledge I have been acquiring by solving some of the bugs reported by the end users.

One of the first Django-based projects I laid my eyes on is the [official website for Python][3], so without reading much of its code (I am still in the process of reading it thoroughly for the first time) I jumped immediately in the issue tracker to see if there was one simple enough to solve for a beginner like me. In fact, I found [one][4] that _seemed_ quite easy to start with:

![The layout is behaving in a quite bizarre way here](https://cloud.githubusercontent.com/assets/1864489/12796759/5bfa94b4-cab8-11e5-971a-fe61cfac4b89.jpg)

It was quite easy to see that something was not going on well with the results of search for events: the strings 'From at' and 'though at' are collapsed one on top of the other, they are not where they are supposed to be, and there is no indication of the start and end date and time of these events.

What was a little bit _less_ easy to see for a beginner was:
* there is an [easy way][5] to setup a development environment to start working on the problem but it relies on Ansible, which is not available under Windows (which is installed on my laptop) unless you install Cygwin and a whole bunch of packages, and after doing all of this I was still not able to spin up and provision the VM auto-magic-ally;
* there is a [manual way][6] to setup a development environment (which I ended up using), but it took a lot of trial-and-error cycles to understand that I had to download the 14.04 version of Ubuntu, some older libraries (as the project is based on Django 1.7), and so on and so forth;
* the search is implemented through [Haystack][7] and [Elasticsearch][8] (both of which I have never used in the past), so it took me some time to install and configure them properly.

After a week of understanding and failed attempts, I figured out that the problem with the positioning of the two strings was caused by the reuse of a CSS class designed for another page (in which, effectively, they are displayed in the left side of their container) and that, in the case of the missing start and end dates, the problem was that they were being retrieved in the wrong way from the Haystack results. So, without further ado, I went on and created a [pull request][9]... in fact, my first pull request ever!

Since it was so [well-received][10] from the project's mantainer, I felt motivated to try go through the process once again... but this time I aimed a little higher: I chose to work on an [issue][11] reported by [Guido van Rossum][12] himself! The misbehaviour in this case was that, when the width of the browser window was under a certain value, a spurious portion of the blue background was shown, and this also caused the horizontal scrollbar to appear. One of the contributors suggested that it was likely to be caused by the implementation of the dropdown menus and, after some investigation in the CSS definitions, I was able to confirm that this was indeed the case:

{% asset_img dropdown-overflow.jpg "The dropdown menu exceeds the margins of the layout, causing the overflow" %}

Interestingly, the issue appeared only when the dropdown menus associated with the Socialize and Sign In were hidden, and would promptly vanish as soon as the dropdown menus were shown. From this observation, I simply changed the way in which these menus are hidden (removing them effectively from the page layout), so that the problem could not (and would not) show up _by design_.

After some testing and with the blessing of the [Benevolent Dictator For Life][13], my [pull request][14] was finally merged and deployed onto the production server!

**TL;DR (long story short, in today's Internet lingo): I fixed a couple of bugs in the official website of Python, I enjoyed the whole process, the reception was better than I expected, so I will probably do it again in the near future.**

[1]: https://www.djangoproject.com/
[2]: https://github.com/
[3]: https://www.python.org
[4]: https://github.com/python/pythondotorg/issues/883
[5]: https://pythondotorg.readthedocs.io/install.html#vagrant-setup
[6]: https://pythondotorg.readthedocs.io/install.html#manual-setup
[7]: http://haystacksearch.org/
[8]: https://www.elastic.co/downloads/elasticsearch
[9]: https://github.com/python/pythondotorg/pull/1036
[10]: https://github.com/python/pythondotorg/pull/1036#issuecomment-268206820
[11]: https://github.com/python/pythondotorg/issues/731
[12]: https://gvanrossum.github.io/
[13]: https://wiki.python.org/moin/BDFL
[14]: https://github.com/python/pythondotorg/pull/1047