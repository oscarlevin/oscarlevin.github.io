---
layout: article
title: Typeset your math homework
tags: tech tex teaching
---

Typing your math homework has two main advantages over hand written work.  First, typeset mathematics is easier to read, for which your professor will thank you.  Second, it is easier to edit, correct, and even write mathematics the first time when you are typing, since you can insert or delete content as you go.
<!-- more -->

# How to typeset mathematics

The main challenge is that you need to figure out how to type all those symbols! 
Although word processing programs like Word or Google Docs allow you to insert "equations", if you want to do any amount of serious mathematics, you will want to use a *markup language*.  You type your document in plain text using the syntax (markup) of the language, and then compile your text document into a nicely formatted pdf or webpage.  

Here we will consider two such languages; markdown and LaTeX.  Here is the short version: Markdown is easier to get started with, but gives you less control over the structure and format of your document.  LaTeX has a steeper learning curve but is the gold standard for writing math or science papers, and you will need to learn the LaTeX commands for math symbols to put them in Markdown anyway.

To get started right away, you can try online editors.  For Markdown, I recommend [StackEdit](https://stackedit.io/).  For LaTeX, there is [Overleaf](https://www.overleaf.com?r=26028ffe&rm=d&rs=b).  Both have good instructions on how to get started.

Not sure which to use?  Let's look at the features of each a little closer.

## Markdown

This document you are reading has been written in markdown.  It is a very basic syntax for plain text documents that allows you to specify basic formatting easily.  For example, to get title headings, you write something like `# Main Title`, or `## SubHeading`.  You can get italic text using `*italic words*`.  Lists are easy as well.  See [this link](https://www.markdownguide.org/basic-syntax/) or many other guides for an overview of what you can do.

So you write your document in a basic text editor, and then compile it into your output format, which could be HTML (for the web) or a pdf.  This can be done on your computer, or using a online tool.  Checkout [StackEdit](https://stackedit.io/) or [markdown notes](http://markdownnotes.com).  Both tools are free and have nice interfaces.  To get a pdf (to print or submit electronically), you can print the output and select "save as pdf".

Both the editors above allow you to typeset math by calling LaTeX commands, although the format is slightly different (using `$` or `$$` to start or stop the "math mode").  Note that this is really an add-on to markdown, so other editors you find might or might not have the feature.

If you use one of the online editors, you can download the "source" files (it will have a `.md` file extension).  One reason to do this is to use the program [Pandoc](https://pandoc.org) to convert your markdown to other formats, including...

## LaTeX

Like Markdown, LaTeX is a markup language.  So you type your document in a text editor, and then compile it into a pdf (or other format, but mostly pdf).  It used to be that this required that you install LaTeX packages on your computer (which isn't hard, but is a big install).  Now you can use an online editor called [Overleaf](https://www.overleaf.com?r=26028ffe&rm=d&rs=b).  There you can type your documents and compile inside your browser (and then download the pdf).  It also has a bunch of templates you can use (including homework templates) to get started.

That overleaf has templates is good, because there is a lot of baggage in a LaTeX document that tells it how to format everything.  When you are starting out, you don't need to worry about this (thanks to the templates).  And all of this is really nice if you want to do anything beyond simple documents.  For example, you can create numbered theorems (LaTeX keeps track of your numbers) and get nice proof...qed formatting around your proofs.  You can also define macros, so that instead of typing `\mathbb{N}` to get $\mathbb{N}$, you can write `\N` each time.

Using Pandoc, you can convert other formats, including Markdown and Word, to LaTeX.  You could upload this to Overleaf, or compile yourself.

If you want to set up your computer to compile LaTeX documents, you can do this using MacTeX (for Mac OS) or MiKTeX (for Windows).  Other options can be found [here](https://www.latex-project.org/get/).

If you are a little adventurous, or plan to write scientific/mathematical papers in the future, it is worth figuring out LaTeX ASAP!  There are some good tutorials online (for example [this site](https://www.latex-tutorial.com/) looks to have lots of good resources).

## Useful tools

* [MathPix Snip](https://mathpix.com/).  Not sure how to write a math symbol in LaTeX?  MathPix let's you take a screen capture or photo with your smartphone of math and will translate it into LaTeX.
* [Detexify](http://detexify.kirelabs.org/classify.html).  You can draw a symbol with your mouse (or on your smartphone) and get suggestions of the LaTeX code to create that symbol.
* Modern Text Editors.  If you want to write markdown or LaTeX on your own computer, you should learn how to use a real text editor.  I like [VS Code](https://code.visualstudio.com/), and used to use [atom](https://atom.io/), both of which are free.  Another option sis [Sublime Text](https://www.sublimetext.com/).  All of these have extensions/plugins for markdown and LaTeX that can help you speed up writing.

## Other options

### Jupyter notebooks

A jupyter notebook is a document that contains both executable code and regular text, which can be written in markdown.  To run a jupyter notebook, you can install [Anaconda](https://www.anaconda.com/distribution/) or [SageMath](http://www.sagemath.org/) (depending on whether you want to execute Python code or Sage code).  There are also some online jupyter notebook servers.  [CoCalc](https://cocalc.com) is a very good one, but the free version has performance issues.

### Word or Google Docs

Both of these word processing programs allow you to insert math equations using an equation editor.  However, if you plan to insert a lot of math, this can be slow.  To speed it up a bit, learn the keyboard shortcuts.  On Windows, the MS Word equation editor can be brought up using `alt+=`.  The Google Docs equation editor requires `alt+i, alt+e`.  The equation editor in Word is pretty good about taking LaTeX math commands and turning them into the correct symbols.  Google Docs only works sometimes.


## Doing the Right Thing

Whatever format you choose, you should use it correctly.  In particular:

* All math should be written in "math mode".  If you have a variable $x$, you should put that inside dollar signs or use the equation editor.  Do NOT leave it as just x, or even just make it italic.  Do you see the difference: *x* vs $x$.  Which looks more like math?  What about *f(x)* vs $f(x)$?  
* Other formatting should have *semantic* meaning, not just look pretty.  This means that when you want to put a title in your document, you should format it as a title, not format it as larger font and bold.  If you use Word, select Heading or Subheading.  If you use LaTeX, type `\section{your title}`.  In Markdown, use  `## your title`.  This way, if you ever want to convert your document to another format, you have some hope of it working.



