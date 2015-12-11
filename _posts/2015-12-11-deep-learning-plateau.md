---
layout: post
title: Has deep learning reached a plateau in computer vision?
description: "Has deep learning reached a plateau in computer vision?"
comments: true
---

Just after CVPR 2015, I described the exponential growth that deep learning had in vision paper (see the [original blog post]({{ site.url }}/deep-learning-scraping/)) by analyzing the paper titles.<br>
<br>
Since the CVF just released the papers [here](http://www.cv-foundation.org/openaccess/ICCV2015.py), I updated the script and run it.
You can also find all papers in BibTex format in [this folder](https://t.co/vMDwLVoypE).
<br>
<br>
Here the result in the command line:
{% highlight python%}
> python scraping_cvpr.py
CVPR2013:  0.85%
ICCV2013:  1.54%
CVPR2014:  3.70%
CVPR2015: 14.45%
CVPR2015: 14.45%
{% endhighlight %}

And the plot:
<br />
<br />
<img align="middle" width="350" src="{{ site.url }}/images/deep_learning2.png" alt="...">
<br />
<br />

Surprisingly, the percentage of papers with some of the deep-learning keywords is the same for ICCV 2015 than for CVPR 2015. Does this mean that deep learning has plateaued in computer vision?<br>
<br>
I feel that the general opinion will be that the field is still far from reaching a plateau. My interpretation for the titles not increasing is that deep learning is almost taken for granted in some sub-fields, so some authors do not feel the need to specify it in the title.

