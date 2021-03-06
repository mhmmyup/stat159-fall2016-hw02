#Hi (Or, Abstract)

This is a general tutorial and explanation of how to use certain programs, packages, and file manipulation systems to create a reproducible workflow. Now, what may immediately come to your mind is: What does it mean for something to be reproducible? What is a reproducible workflow? And why does it matter?  

Put simply, the reason we put all this effort into making something "reproducible" is an ultimately simple aim: we want to create works and code and files that can be reassembled, piece by piece, and can be re-ran or re-executed from anywhere by anyone, such that anyone can follow the process we use to make reports and research and do it on their own. We, as programmers, statisticians, researchers, and academics, can sometimes forget the work that we have founded our study on, or that we, too, can contribute in a meaningful way to advancing the sum total of accessible and parsable human knowledge. We can help out everyone by using just a few tools to make our research process reproducible, and thus, far more useful!

Principles of reproducibility are far from the norm in computing practices, and may seem daunting or a hassle at first. Learning these tools and how to use them quickly and efficiently to best suit the reproduction process will make implementing the reproducible workflow simplified and logical. Hopefully we, as a programming culture, can come to see the importance of systems like this to make 

----


###Me (An Introduction)

If you were curious, I'm a statistics student at UC Berkeley who cares a lot about **making the research process more accountable.** I've thought endlessly about how tempting and easy it may be for researchers to exaggerate or fib a little bit in their findings to make them seem a bit grander or important, to make money, etc. This is a huge issue that I think is going largely unignored! 

![UC Berkeley Reproducible Data Science](../images/stat159-logo.png)

This is my first foray into writing something like this which could be used to make better the research process, but it definitely won't be my last.  
Tutorials like these will hopefully serve to make more mainstream the importance of reproducibility in programming research and academia, just as the principles are core in the sciences and other fields. Computing is lagging behind when it comes to reproducibility, slowing the accumulative gains in knowledge that we could be facilitating if we were only sharing our code and making our research reproducible for others to alter, implement, study, and engage with. How are we supposed to advance if not together?

---


###Now what tools, exactly?

To quickly lay a framework for this tutorial, we'll be going over a few different tools to make the computing process of research reproducible. In specific, the tools we'll be looking at are

* bash
* markdown (and online platforms)
* pandoc
* git
* github
* Make/Makefiles 

I used very minimal text editing software, but to make this I used a light combination of nano, a very lightweight, simple, in-line bash text editor for the start of the Makefile, and Sublime Text (which is difficult to set up with Windows 10 bash) to do more complicated editing. But there was very little coding done in the process of making this tutorial so the text editors aren't particularly relevant. Sublime seems promising, though, and this was actually my first time ever using it!

Even from the get-go, I am writing this file on an online markdown site so that I can see what my markdown will look like in real-time. The site I'm using is [http://markdownlivepreview.com/](http://markdownlivepreview.com/)  
It's one of the better live markdown tools out there because it's more stripped down - it (for the most part) only shows the markdown syntax that is universally rendered and recognized across the web and other platforms. More about markdown later!


####Let's go!

Hopefully this guide/blog/tutorial will make these tools more friendly and simple to use. We'll mostly be looking at the parts of these systems which specifically help in creating a reproducible workflow, so as to not distract you with irrelevant information and commands which are not immediately pertinent. Let's have fun and get started!



--------






##Tools (A discussion)



###Markdown


As I said earlier, this file I'm writing is a markdown file, which is a specific implementation of the "markup" language, a text formatting/rendering software which serves as a standard method of stylizing and formatting text. Importantly, it can be rendered universally in many different file types across all computers, on web browsers, and more. It's a crucial way in which we can write text and have it be parsable but also a bit more - we can include links and images to bolster our writing. And these images can be pulled from other files in our repository which we have shared, thus, with markdown, we can bring everything together, across files, to present a followable narrative. Using another tool which we'll discuss later, **pandoc**, we can convert easily and fluidly from all different kinds of files. We can go from the entirely human-made .md file, which is just text and basic markdown syntax, to a .html file! A webpage from some text!

There's a bunch of basic markdown syntax which I've used to write this paper. I'll briefly go over some main, usefull stuff.

* The section headers that I've been using. 
     - Put from one # to six ###### at the start of a new line to make a header, from largest (#) to smallest (######). Don't put more than six! It may not render properly on certain pages and just show up as seven hashtags. Gross!
* Basic text formatting 
     - Bolding: two \* on either side of your desired-to-be-bolded text. 
     - Italics are the same, but one \*. 
     - Code: Four spaces at the start of the new line. We'll see some of this later!
     - Quotes: a \> at the start of a new line.
* Links, images, more!
     - A link in markdown follows a pretty simple syntax. \[Text that will be seen and clickable]\(Desired link to webpage)
         - [Click me for a link to google!](www.google.com)
     - An image is a very simple adjustment to our previous link syntax. Just add an ! to the beginning, i.e. !\[]\() This will render an image inline, on the page. 
     - We can also use images in our shared repositories or local files! Just make sure to use proper . and .. relative pathways!
         - ![Markdown logo](../images/markdown-logo.png)
* These lists
     - Bulleted - Just put a \* at the start of each new list entry line. 
     - For these indented lists, put about four or so spaces before another \- or \* at the start of a new, sublist element.
     - For ordered ones, put numbers! These can be kind of tricky syntactically so just fiddle around with it and it should work eventually.
* Of course, there's more to markdown, but this is a good basic overview of some simple syntax. We can quickly see that being able to enrich our text beyond that of just a textfile can be very powerful, and together, a markdown file can bring all the elements of a project together, in a readable, parsable, implementable way. 


###Pandoc


![Pandoc logo](../images/pandoc-logo.png)


I mentioned that markdown files can be easily converted from one type to another, human to .html. This isn't a trivial process inherent to markdown, however. **Pandoc** allows us to convert these files freely by smartly taking into account the original file's syntax and transforming it into the end, desired file's syntax. It can be done pretty easily using **bash**. While I won't get into the specifics on how to use the bash shell, we will show how to use pandoc, in the bash shell, to convert filetypes.

    $ sudo apt-get install pandoc

First we actually need to install the package. For simplicities sake, let's assume we're in the working directory of the file which we want to convert, testfile.md. Let's say we want it to be converted into a .html. This will take only one line in the terminal with pandoc!

    $ pandoc testfile.md -s -o testfile.html

Let's break that down. The first portion, `pandoc` signals to the bash shell that we're going to be using commands within the pandoc library. Then, we just put our starting file. 

*It can be located somewhere else, we just have to refer to it with . and .. and / relative pathways. This shouldn't be too complex, but very quickly: "." refers to your current directory. ".." refers to the directory one step removed, closer to the root directory. We can use a combination of ../directory/file.md and directory/file.md to refer to files anywhere within our drive. *

Anyway, let's get back to the pandoc commands. We then follow the file with two relatively standard options, `-s` and `-o`. These modify the standard pandoc conversion command to be more usable and better for our purposes.   
`-s` indicates that we want to create a "standalone" file, which isn't done on default for .html files. This will mostly help rendering be more reliable.   
`-o` tells pandoc that we want to dump the conversion code into a file and not just into the terminal standard output. This makes pandoc useful! It will convert the original file into a standalone type, then, it looks where to put this converted file syntax. `-o` lets it know to look for a file to put this in. So, we follow it up with our end filetype that we desire. Since it's a .html, pandoc parses this and knows it should use the .html conversion algorithms that it has to make the syntax perfectly transition!

Turning the markdown file, which can have content from the web, code blocks, images, and more, into a sharable webpage or other filetype is incredibly powerful! However, pandoc just ran from the command line isn't too convenient. We'd have to type in the commands every time we make a change to the original file. We can expedite that process!


###Make


Make. Make is a useful tool which enables us to basically program sets of bash commands to an easily executable macro. This is done pretty simply. Let's assume we have make installed. We want to make a macro to speed up some of the processes that we're doing - perhaps we're writing a paper and want to make incremental saves and additions, creating a final product we can check to see how it's coming along. Markdown can be finicky! And we could also notice other errors or issues with our code chunks in the markdown file, etc. Make lets us enter in a sequence of bash commands, in a macro format, which we can then easily and simply execute. 

We begin with The Makefile. This is the file in which we store our macros. The syntax is simple, but we still have to make sure we know all of it to actually use the make macro process. The most simple syntax of the makefile is

    target:dependencies
    	bash command(s)

Let's go over each part. 

* The `target` is the file we wish to create with the macro. This is not always a file, though, as the Makefile has a few special targets to make the process even more efficient. Two common built-in targets are `all` and `clean`. I'm using both in the Makefile I'm using to make this paper! The all target lets us show our "main" file which we want to iterate upon every time we run the macro. Perhaps there's files that aren't worth remaking every time, or the makefile is complicated. This lets us show the file which, at the minimum, the makefile must run through enough macros to create. We put these main files as the dependencies of the all target, with no bash commands. The clean target, on the other hand, has no dependencies! We can use this to simply delete interim or problematic files easily with the make command.

* The dependencies are the files which we will use in the macros to make our end file. We have to include all of them or the makefile won't know how to parse our commands or where to find the files. This listing can be pretty long, so Makefiles allow us some leeway here to use wildcards or variables to refer to more than just individual files at once. However, the syntax is a bit tricky and I'm not completely confident in it, and I don't want to spread misinformation. Here's a handy Make tutorial :) [Gaston's Make Tutorial](https://github.com/unix-tools/tutorial-makefiles)

* The bash commands are simply the lines of terminal code which make will run while it works to create the end target file. Now, this is where make becomes powerful: we can use packages or anything of all sorts which we would use directly on the command line! If you didn't see it coming, we can use `pandoc` here!

Now that we have the makefile, and all the pathways and stuff are set up, in the terminal we can simply enter `make`. This should parse through the Makefile and do what we want! It should be simple to see how this allows for reproduction - we show, exactly, how we made certain files, what the pathways are, what the process was - and we let others in on it! They can execute the makefile themselves or examine what went in to every file. Nifty! 

Make also lets us continually and incrementally update our files, clean them out, then update them again. Why would we want slow, incremental additions to files while we're working on them? 



###Git and Github

![Git logo](../images/git-logo.png)

Git, in combination with Github, allows us to keep track of how our files are doing, what's been changed, document changes, and, ultimately, share the files and their repositories with the world. This is understandably very powerful in terms of reproducibility - we can interface with the bash terminal, our files, and the internet all at once, document the changes we've made, and push them out to public directories on Github for all to see. Github is the website which is the online side of git - what we do with git in our terminal, in the end, is pushed to a repository on the Github website, which we can share. 

Again, we'll assume git is installed. Then, we'll initialize our directory as a "git repository" by doing `git init`. The basic git process is such:

     $ git status
     $ git add (files)
     $ git commit -m "message"
     $ git push

We don't just automatically share everything we do, however! Git is a conscious process through which we add files to a queue, decide that the change is good with a commit and a commit message, then push to our online Github repository. So, we select the files we desire to update or add, then decide if we're ok with it, then push it to Github. We can document and comment each step of the way! We can then share this github repository with the world!

One thing though - we have to set up the github repository, too. Git doesn't natively know where we're going to publish this stuff! This process is still confusing for me, so hopefully I'll be able to explain it.

    $ git remote add origin (github link.git)
    $ git remote -v
    $ git push origin master

You may need to fiddle with this a bit to get it working at the start, but this is the basic process to initiate the github remote repo and let us push to it. The `git remote -v` command lets us see what we're connected to and make sure everything is ok! Once we do this, `git push` after the commit will just push right to the repo we want until we decide to change it. 

Thus, Git and Github together let us share our files and directory systems with the world, through small, deliberate iteration and care. 


![Github Logo](../images/github-logo.png)


This is deceptively powerful and ultimately one of the core parts of the reproducibility process. Without an easy to use online platform which we can interface with, and is so built up, projects and reproducible actions would be a good deal more arduous. While the github online webpage is definitely a work in progress, and can be difficult to use, the git library on bash is simple, understandable, and allows us to have a huge amount of controll over what we share, how we frame it, and when we'd like to do so.






##So? (Conclusions)

The reproducibility process is absolutely core to good research behavior. But it isn't perfect and can be challenging. These tools are not completely intuitive and can be a pain to set up, but once you get them working, you can see the power in every single one.

The makefile allows me to make small iterations to files which are one of many used in a larger file and then easily alter the end file as I please. Pandoc lets me write in markdown and then convert it to a webpage I can share with the world. Markdown lets me frame my thoughts and intersperse them with code, images, links, and more. And git with github give me a procedue within which I can slowly iterate my changes and share them with the world. Once they start coming together, it's a very liberating experience. Things can go smoothly and all my iterations are tracked and reproducible. I don't have to worry about forgetting to update a certain file if it uses other files to make it. Everything works together in a cool harmony!

I had a good deal of fun writing this and it helped reinforce to me how reproducibility can improve accountability. I think lying or obfuscating research is a contemporary cardinal sin, so I hope tools like this become more popular and used by all.

Github is still a pretty annoying platform, so I'm glad that git lets me not even think about it at all besides connecting to it! I always get confused on the site. Very unintuitive. Good thing it doesn't matter too much.

I talked a bit about Windows 10 bash and makefiles with other people to hash out my thoughts and work on them together. Those two can be finicky and you have to do everything just right, so I'm glad I had people to bounce ideas off of.

This didn't take too long as a whole, but I bluescreened in the middle of it :( So I lost a good deal of work. This was actually a great lesson, while working on this project, on why iteration and documented changes matter! I lost a ton because I wasn't saving and commiting as much as I should've. Lesson Learned!

I hope this tutorial will be a good reference for me in the future and was a good writiing exercise to really have me negotiate with why these tools are useful and how to best use them. Thanks for reading!