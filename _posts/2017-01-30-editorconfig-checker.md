---
layout: post
section-type: post
title: editorconfig-checker
category: tech
tags: [ 'programming', 'php' ]
---

[![Logo](/img/editorconfig-checker.png "Logo")](https://github.com/mstruebing/editorconfig-checker)
[https://github.com/mstruebing/editorconfig-checker](https://github.com/mstruebing/editorconfig-checker)

If you work with several people on the same project it often occurs that
you will see different indentation sizes. Everyone who is a programmer knows 
this kind of pain.  
So someone thought lets make a file which the different text-editors 
can read and indent their code blocks like defined in that file.

But what if the humans who are using the text-editors didn't tell their
text-editor(or IDE) that it should read that file?
Then it changes nothing and the old pain is back.  
You have to enforce the rules! But if you want to enforce them you need tools which check if the rules are
followed.

There are some tools out there which promise to solve the same issue as me, but not a single one in the php/composer world, so I made one. :)

Note that this is a very early stage and I tested it while I was coding.  
\- I'm writing this at version 2.2.6 - yes, I'm following semver -   
Some bugs are already fixed but I'm sure I've not found all of them.
So I hope I will try it out in some projects and find some bugs which I could fix, or maybe there are none. :)

I would be happy if someone of you would be trying it too and if you encounter any bugs or issues please don't hesitate to contact me or open an issue, this would be really helpful.

Feature requests are also welcome.
And of course - pull requests ;)

At this time I think of one feature which is to exclude some files/folder from a pattern for example `node_modules` or `vendor`.
And of course I want to write tests .....

I follow the PSR-2 coding standard and enforce this rule within my travis build where I also do a self-check of this tool.

I would love to hear any feedback from you who is reading this and of course stars stars stars for the repository. :)

cu <3
