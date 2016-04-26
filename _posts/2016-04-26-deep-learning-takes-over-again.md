---
layout: post
title: "CVPR 2016: Deep learning takes over again?"
description: "Has deep learning reached a plateau in computer vision?"
comments: true
---

This is my customary update of percentage of <i>deep-learning papers</i> in the major vision conferences. At CVPR 2015, I described its [exponential growth]({{ site.url }}/deep-learning-scraping/), and after ICCV 2015 I wondered whether it had [plateaued]({{ site.url }}/deep-learning-plateau/).<br>
<br>
Since the CVF has not released the papers yet, I had to adapt my script to take the titles from the [program](http://cvpr2016.thecvf.com/program/main_conference).
You can download all titles in TXT format in [here](https://www.dropbox.com/sh/nhsric6bksopot3/AADz3BWN6I8i1VsDNLOpvdDAa?dl=0) if you want to play around.<br>
<br>
And here the evolution of the results:
{% highlight python%}
CVPR2013:  0.85% (  4 out of 471)
ICCV2013:  1.54% (  7 out of 455)
CVPR2014:  3.70% ( 20 out of 540)
CVPR2015: 14.45% ( 87 out of 602)
ICCV2015: 14.45% ( 76 out of 526)
CVPR2016: 23.79% (153 out of 643)
{% endhighlight %}

And the plot:
<br />
<br />
<img align="middle" width="350" src="{{ site.url }}/images/deep_learning3.png" alt="...">
<br />
<br />

So the plateau was in fact only a short pit stop to take over again. Maybe it saturated in the <i>classical</i> areas such as object detection or image labeling and is now expanding to the rest of the topics?<br>
<br>
Here the code for you to try:
{% highlight python %}
#!/usr/bin/env python
# -*- coding: utf-8 -*-
from HTMLParser import HTMLParser

# Global variables
on_strong_tag = 0;
all_titles    = [];

# Create a subclass of HTMLParser and override the handler methods
class MyHTMLParser(HTMLParser):
    def handle_starttag(self, tag, attrs):
        global on_strong_tag
        if tag=='strong':
            on_strong_tag = 1
    def handle_endtag(self, tag):
        global on_strong_tag
        if tag=='strong':
            on_strong_tag = 0
    def handle_data(self, data):
        global on_strong_tag, all_titles
        if on_strong_tag == 1:
            all_titles.append(data);


# Parse the file (I erased the orals and spotlights,
#                 and removed all '#&' and '&')
parser = MyHTMLParser()
f = open('cvpr2016.html', 'r');
parser.feed(f.read())


# Search for the 'deep'-inducing keywords
conf = 'CVPR2016'
keywords = ['deep', 'cnn', 'convolutional', 'neural network']
count = 0
for title in all_titles:
    for kword in keywords:
        if title.lower().find(kword)>=0:
            count = count+1
            break
percent = count/float(len(all_titles))*100
print("%s: %.2f%% (%d out of %d)" % (conf, percent, count, len(all_titles)))
{% endhighlight %}