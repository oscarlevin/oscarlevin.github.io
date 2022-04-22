---
layout: article
title: Creating PreTeXt course materials with ease
tags: PreTeXt textbooks
---



The PreTeXt document system is a popular choice for authors of open source math textbooks, since it provides highly accessible interactive online versions in addition to a variety of other formats.  Recent work has made using PreTeXt much simpler, to the point that instructors can now easily use it to prepare course materials on the go.  

The page contains the content of a talk given at the Rocky Mountain Section of the MAA spring 2022 meeting.  In the talk, I demo just how easy it is to get set up and create a new PreTeXt course website which can easily be updated throughout the semester.  We also explore some of the exciting new features of PreTeXt that will soon allow even more interactivity.

<!--more-->

## Why PreTeXt

Say you want to create a set of course materials, including lecture notes, homework assignments, group activities, and maybe even interactive demos.  You could do most of this in LaTeX, which could generate PDFs to post online or print out for your class.  Or you could try to write everything inside Canvas (or another LMS) so you can link between things and organize them.

But PDFs are notoriously non-accessible and difficult to read on a small screen.  Canvas is hard to work in and non portable.  There must be a better way!

There is: [PreTeXt](https://pretextbook.org/).  Imagine being able to write up your content using some simple markup and in minutes generating highly accessible, feature-rich HTML versions of your materials.  Then take that same source material and generate PDFs to print or download for offline use.  At the end of the semester, your students have a website or ebook of their "textbook" that includes exactly the content of their course.  Advanced students might even be able to contribute directly to the course materials.

I called the HTML output *feature-rich*; some of the most useful features include:

* Excellent cross-reference and index support: links open up "knowls" that contain the content of the reference (all automatic).
* Hints, Answers, and Solutions to examples and exercises are hidden to avoid spoilers and improve reading flow.
* Easily embed youtube videos, geogebra applets, jsxgraphs, WeBWorK exercises, SageCells, and more.

A few examples of these features and what PreTeXt output can look like:

* [Discrete Mathematics: an Open Introduction](http://discrete.openmathbooks.org/dmoi3/sec_counting-addmult.html).  
* [PreTeXt (annotated) Sample Article](https://pretextbook.org/examples/sample-article/annotated/section-interactive-authored.html) for interactive features (if you click on the "view source" links, you can see what was authored to make generate that section of the page). 
* [Abstract Algebra: Theory and Applications, Remixed!](http://math.oscarlevin.com/math322-spring21/ws_groups-RSA-lab.html). This shows both how you can modify an OER textbook for your course, and insert an activity in which students can execute Sage code right in the browser.
* [Student created Graph Theory book](https://math.oscarlevin.com/math795-fall20/).  Using open pedagogy, students all contributed to a shared "textbook" for our graduate course.

While this vision has been possible for a long time, recent development has made using PreTeXt much easier, both in the authoring and "publishing" steps.  Below I outline what you need to get started and a simple workflow to get your course website up and running.

## Prerequisites

Files written in PreTeXt are just plain text XML documents, so you can start writing them with no additional software beyond a text editor.  However, if you want to compile these documents into HTML or PDF or another format, you will need some additional tools.  The setup I suggest here is not the only way to proceed, but I believe it is the easiest (and works basically the same on Windows, Mac, or Linux).

Download (or make sure you already have) the following software:

* [Visual Studio Code](https://code.visualstudio.com/).  Any modern text editor would work here, but VS Code has an extension I wrote for PreTeXt called "pretext-tools", which provides syntax highlighting and auto-complete "snippets".
* [Python](https://www.python.org/downloads/), version 3.8.5 or better.  If you are installing this on Windows, make sure you check the "Add Python to PATH" checkbox.
* [LaTeX](https://www.latex-project.org/get/).  This is needed if you want to create PDFs from PreTeXt, or if you want to include images written directly into your source code using tikz.

### Getting PreTeXt

Note that the software above doesn't include PreTeXt itself.  Let's get this set up next.

1. Open VS Code and use shortcut [Ctrl+&#96;] (on a Mac, replace "Ctrl" with "Cmd" in all shortcuts).  This opens a terminal where you can type commands.
2. To make sure you have Python properly installed, enter the command `python -V`.  If you get back "Python 3.8.5" (or a newer version), then you are good to go.
3. Enter `pip install pretextbook`.  
4. Now if you type `pretext --version` you should get at least "0.6.3" as the output. 

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

There is lots more to explore, so check out the [official documentation](https://pretextbook.org/doc/guide/html/guide-toc.html) for more features and suggestions about how to get started.

## Publishing your materials on GitHub Pages

So far, everything we have done has been on our own computer.  To share the site with our students, we need to host it somewhere.  If you already have a website hosted somewhere, you can simply upload the contents of the `output/html` folder to your website.  If you don't have this setup, there is a very easy way to publish your site using [GitHub pages](https://pages.github.com/).

Here is what you need to do:

* Sign up for an account on [GitHub](https://github.com/), if you don't already have one.
* If you are on Windows, you will need to install [Git for Windows](https://gitforwindows.org/).
* [Create a remote GitHub repository](https://github.com/new); you will be importing your PreTeXt book that you already created, so skip the "initialize this repository with:" step.
* Doing this should take you to a page with instructions for quick setup. We will follow slightly different steps than described there, but make note of the url (something like `https://github.com/username/mybook.git`) for your repository.  To initialize our local version of the repository and link it to GitHub:
  * From the terminal in your VS Code window, type `git init`.
  * Enter `git remote add origin [url]`, where `[url]` is the url you copied from the instructions page.
  * Enter `git branch -M main`
  * Enter `git add .`
  * Enter `git commit -m "first commit"`
  * Enter `git push -u origin main`
* Now we can simply enter the pretext commend `pretext deploy`.  This will put all the html in a `docs` folder, and push that to github.  You will do this every time you want to publish updates.
* On GitHub's website, navigate to your repository, click on "Settings" and the "Pages" (left menu, bottom of "Code and automation"). Using the dropdown menu under "Source", select "main".  Then select "/docs" as the folder (in the dropdown menu to the right) and click save.  
* You can now click on the url that pops up.  After a minute or two, your site should be live.

Now, whenever you `pretext build` changes and they are ready to be uploaded, just doe a `pretext deploy` and your students will have access to any changes you made.
