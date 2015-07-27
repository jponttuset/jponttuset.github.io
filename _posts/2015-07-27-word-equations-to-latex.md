---
layout: post
title: Word to LaTeX, with Equations
description: "How to get the LaTeX code, including equations, out of a Word document."
comments: true
---

Maybe you have some old documents with nasty equations written in Word, but now you need to re-use them in LaTeX (maybe for your dissertation), and of course you don't want to re-type everything.
Thankfully, there exists [writer2latex](http://writer2latex.sourceforge.net) that will help you do that. Here are the steps:

1. writer2latex takes a LibreOffice document as input, so first thing is to **download and install [LibreOffice](http://writer2latex.sourceforge.net)**, open your Word document (`.docx` or `.doc`) and **save it as `.odt`**.


2. Then **download and install [writer2latex](https://www.libreoffice.org)** and read the instructions on how to run it. In Unix, for instance, it involved changing the execution permissions of the binary: `chmod +x w2l`.

3. Run the code: 
```./w2l -ultraclean Text.odt Text.tex```
We use the `-ultraclean` option to get rid of all formatting, since <span class="latex">L<sup>a</sup>T<sub>e</sub>X</span> will take care of that.
It is probable that the generated `.tex` won't compile at first, so I recommend you get the parts you're interested in by pieces into your final document.

Big kudos to Henrik Just!