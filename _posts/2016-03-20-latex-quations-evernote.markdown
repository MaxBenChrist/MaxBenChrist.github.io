---
layout: post
title:  "Using LaTeX equations in Evernote (on Mac OS X)"
date:   2016-03-20 17:00:00 +0100
categories: LaTex, Evernote
comments: True
tldr: I will show you how to convert LaTeX snippets into nice equations in your Evernote notes
---

__TLDR: I will show you how to convert LaTeX snippets into nice equations in your Evernote notes__

---
<br>
I started using Evernote as my digital brain to store all information I want to keep.
As a statistician my research notes often contain complex equations and I am used to store those equations as LaTeX Code.

But there is no native support for LaTeX in Evernote, only a [request](https://discussion.evernote.com/topic/16445-request-support-for-latex-formulas/?page=1) on the official forum. There is an addon called [eatags](https://eatags.com) that is apparently able to [understand LaTeX](https://www.evernote.com/shard/s216/sh/f2b5d32d-7941-4473-bb94-21fbd55ae117/6f7b872883ab019ba763de2c9cd0ac3f). But you have to register yourself to use it, which is why I did not give it a try.

Instead I found an easy way to render LaTeX code snippets into nice equations in your Evernote notes. At least if you are using Mac OS X ;\-\). 

# Settings

First make sure you have [LaTeXiT](http://www.chachatelier.fr/latexit/) installed.
It is part of the [MacTex](https://tug.org/mactex/) distribution so changes are good you already have it on your Mac.

Then we have to make sure that LaTeXit is exporting its pictures as png.
This is necessary in order to insert the images into the free version of Evernote.
So open LaTeXiT and change the export format of its pictures to .png:

![Set LaTeXit to export images as png](/images/equation_evernote_1.png)

Now we have to set the global shortcut.
To do so, go to to your global system settings. 
Switch to the keyboard panel and under "services" select a keyboard shortcut to convert a selection of LaTeX code into a nice equation image.

![Choose shortcut](/images/equation_evernote_2.png)

As you can see in the upper screenshot, I picked "cmd + option + shift + L" as the shortcut.

Now are ready to use LaTeX equations in Evernote!

# Using LaTeX equations in Evernote

Just write your Evernote note as usual. 
Add some LaTeX Code to the note.
Then if you want to convert a LaTeX equation into an image you just have to select the LaTeX snippet

![Mark the text](/images/equation_evernote_3.png)

and press your shortcut.
LaTeXiT will remove the selection and insert an image of the equation into the note as seen in the next screenshot:

![and get an equation image](/images/equation_evernote_4.png)

You do not even have to run LaTeXiT in the background.
If it is not running, Mac OS X will start it for you.
The formating (font size, borders etc.) of the equation can be set in LaTeXiT.  

So enjoy those nicely formated equations in your Evernote notes.



