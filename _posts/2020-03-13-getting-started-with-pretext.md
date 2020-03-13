---
layout: article
title: Getting Started with PreTeXt
tags: PreTeXt textbooks
---

The ColoMATYC 2020 conference is all about Open Educational Resources.  My [talk](/talks/colomatyc2020.html) was about the importance of the source of open source textbooks, which for me, means writing open source textbooks in [PreTeXt](https://pretextbook.org/).

Here are some suggestions for those interested in trying PreTeXt for the first time.  This is a very short introduction; more and better information is available as part of the [official documentation](https://pretextbook.org/doc/guide/html/guide-toc.html).

<!--more-->


## Prerequisites

Files written in PreTeXt are just plain text xml documents, so you can start writing them with no additional software beyond a text editor.  However, if you want to compile these documents into LaTeX or html or another format, you will need some additional tools.  

First, get the latest version of [PreTeXt from GitHub](https://github.com/rbeezer/mathbook) (the repository is called `mathbook`, a remnant from when PreTeXt was called MathBookXML).  You can download a zip file or clone the repository if you know some git.

To process the xml/ptx file, you should use the command line program `xsltproc`.  If you have a Mac or Linux machine, you should have this installed already.  If you have Windows 10, you can install the [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10), which gets you a linux bash shell, in which you could install xsltproc (using something like `sudo apt-get install xsltproc`).  There are other options for Windows; see the [PreTeXt documentation](https://pretextbook.org/doc/guide/html/windows-install-notes.html).

Alternatively, you could work entirely in the cloud using [CoCalc](https://cocalc.com).  You would need to upload a zip of the `mathbook` folder, or if you have a paid subscription, give your project internet access and clone the repository.  The advantage is the CoCalc already has xsltproc, latex, and python ready to go.

If you want to have pdf as the output, that is done via LaTeX, so you will need LaTeX installed.  If you want to generate html and have images coded in your source (such as in TikZ), then you will need python installed to run the "mbx" script.

## Useful tools

While none of these tools are strictly necessary, I find they speed up my work considerably.

* A modern text editor.  I have been using [Visual Studio Code](https://code.visualstudio.com/), but SublimeText or Atom are also reasonable options.  Each of these has a PreTeXt plugin/extension that helps with syntax highlighting and provides "snippets" to speed up writing.  For VS Code, search for "pretext-tools".
* Git or some other version control setup.  I host all my projects on [GitHub](https://github.com/), which has instructions for getting git installed on your computer and how to use it.  This would also make updating PreTeXt easier.
* [Pandoc](https://pandoc.org/) and [pandoc-pretext](https://github.com/oscarlevin/pandoc-pretext).  Pandoc is a very useful program for transforming almost any document format into almost any other.  The pandoc-pretext "writer" provides a way to get PreTeXt files as an output format.  It works just okay, since a lot of markup, from say LaTeX, gets ignored by Pandoc.  Still, it is a reasonable way to start converting LaTeX or word files to PreTeXt.

## Try it!

When you have a PreTeXt article or book, say called "main.ptx", you can process it to LaTeX using the command

    xsltproc -xinclude <path-to-mathbook>/xsl/mathbook-latex.xsl ./main.ptx > main.tex

or to html using

    xsltproc -xinclude <path-to-mathbook>/xsl/mathbook-html.xsl ./main.ptx

Try this using either the sample article or sample book from the mathbook/example folder (replacing "main.ptx" appropriately).  

You might also consider downloading a complete pretext-authored textbook, such as my [Discrete Mathematics](https://github.com/oscarlevin/discrete-book) text, and following the directions in the readme.  In that case, you can avoid a lot of the command line issues you might otherwise encounter by using the makefile, as suggested.