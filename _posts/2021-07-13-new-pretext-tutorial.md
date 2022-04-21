---
layout: article
title: A New PreTeXt Tutorial
tags: PreTeXt textbooks
---

Recent development work on [PreTeXt](https://pretextbook.org/) makes it easier than ever to get started writing high quality open source textbooks (even on Windows).  The following tutorial will get you up and running quickly.  

Some of the information presented here uses very recently created tools not yet part of the [official documentation](https://pretextbook.org/doc/guide/html/guide-toc.html).  Until the documentation catches up, use this tutorial to set up your computer to compile PreTeXt documents, and use the documentation for the latest information about how to organize content inside your documents.

<!--more-->


## Prerequisites

Files written in PreTeXt are just plain text xml documents, so you can start writing them with no additional software beyond a text editor.  However, if you want to compile these documents into HTML or PDF or another format, you will need some additional tools.  The setup I suggest here is not the only way to proceed, but I believe it is the easiest (and works basically the same on Windows, Mac, or Linux).

Download (or make sure you already have) the following software:

* [Visual Studio Code](https://code.visualstudio.com/).  Any modern text editor would work here, but VS Code has an extension I wrote for PreTeXt called "pretext-tools", which provides syntax highlighting and auto-complete "snippets".
* [Python](https://www.python.org/downloads/), version 3.8.5 or better.  If you are installing this on Windows, make sure you check the "Add Python to PATH" checkbox.
* [LaTeX](https://www.latex-project.org/get/).  This is needed if you want to create PDFs from PreTeXt, or if you want to include images written directly into your source code using tikz.

### Getting PreTeXt

Note that the software above doesn't include PreTeXt itself.  Let's get this set up next.

1. Open VS Code and use shortcut [Ctrl+&#96;] (on a Mac, replace "Ctrl" with "Cmd" in all shortcuts).  This opens a terminal where you can type commands.
2. To make sure you have Python properly installed, enter the command `python -V`.  If you get back "Python 3.8.5" (or a newer version), then you are good to go.
3. Enter `pip install pretextbook`.  
4. Now if you type `pretext --version` you should get at least "0.6.2" as the output. 

### Getting pretext-tools for VS Code

From inside VS Code, click on the Extensions button (shortcut [Ctrl+Shift+X]) and search for "pretext-tools".  Install the extension.

## Creating a new PreTeXt project

We are now ready to start a new project.  In VS Code, open the folder that will hold your project (File->Open Folder...).  Use [Ctrl+&#96;] to pull up the terminal.  Then type (in the terminal): 

    pretext new book

This will create a new folder called "new-pretext-project".  Open this folder in VS Code and again pull up the terminal.  Now type (in the terminal):

    pretext build html

This will transform the .ptx files in the "source" folder into html files and put them into a new folder "output".  To preview these files, again in the terminal, type:

    pretext view

You can now view the html version of your new book by going to [http://localhost:8000/](http://localhost:8000/). 

## Time to explore

Now let's edit the PreTeXt document.  The only files you will need to look at (at least initially) are those in the "source" folder of your project.  The root file is called "main.ptx" and this includes (using `<xi:include...\>`) other files.  Open some of these up and start making changes.  

If you have correctly installed the pretext-tools extension, you should be able to start typing "example" and a dropdown menu will appear.  Hitting [Tab] or [Enter] will expand this "snippet" and put your cursor in the right stop to start typing.  Next start typing "statement" and again hitting [Tab] or [Enter] will expand that and put your curser between the `<p>` tags (in PreTeXt, basically all text must be inside `<p>` (paragraph) tags).  There are snippets for almost all PreTeXt tags.  

After editing for a while, save the documents (VS Code has a setting to auto-save whenever you click away from the editor; I find this very useful) and recompile using `pretext build html` again (in the terminal).  Alternatively, for small documents like this, you can run `pretext view -w` to "watch" the files, which will recompile every time you save.
