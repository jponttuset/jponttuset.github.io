---
layout: post
title: Moving a lot of files under Linux (aka messing with MS COCO)
description: "Small trick to move a lot of files, as when working with MS COCO."
comments: true
---


[Microsoft COCO](mscoco.org) is a recent annotated database for object detection, segmentation, tagging, etc. It's one order of magnitude larger than previous similar databases available. Here a comparison of sizes:

| Database  | # classes | # Images | # Objects |
| -------------: | -------------: | -------------: | -------------: |
| SegVOC12  | 20         |   2.913   | 9.847 |
| SBD             | 20         | 12.031|  32.172 |
| MS COCO   | 80         |   123.287  |  910.983 |

So when working with COCO, it's typical to end up having to handle the 123.287 files of results. At some point you may want to move some of them, for instance, those that have a certain pattern in the name, such as *val2014*.

<br />
In a Linux environment and with *mat* files as results, you would typically do something like:
{% highlight text %}
mv *val2014*.mat destination
{% endhighlight %}

This worked flawlessly in Pascal, but in COCO you will get something like:
{% highlight text %}
Argument list too long
{% endhighlight %}

What's the problem? The number of elements that the shell can handle in the arguments is limited, and we may be trying to move a larger number of files. Luckily, we can find a workaround by using ```xargs```:

{% highlight text %}
ls | grep  val2014 | xargs mv -t destination
{% endhighlight %}

The ```ls``` command lists all files and ```grep``` filters the ones we want to move. Then, the list passes to ```xargs```, which executes the ```mv``` command once per member of the list. The ```-t``` option (Note that the ```-t``` option works only on GNU systems) allows to exchange the order of the parameters of ```mv```. More info [here](http://unix.stackexchange.com/questions/128559/solving-mv-argument-list-too-long).