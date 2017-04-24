---
layout: post
section-type: post
title: 'Why I like #2 z'
category: tech
tags: [ 'why-i-like', 'z' ]
---

[z](https://github.com/rupa/z) is a small handy shell script to quickly navigate 
between frequently used folders and directories.

As you can see it is just a ~250 lines of code bash script(including comments and empty lines).
It doesn't do any magic either, what it does is pretty simple. It records all your cd's
and generate a statistic of how frequent which directory is used. Then when you want to navigate 
to a frequent used directory you can simply type `z somePieceOfDirName` and you will be there regardless
where you were before on the file system. It will pick the directory which the most matching name. So for example 
it would be possible to go to ~/Documents with `z Doc` or `z docs` - of course depending on what directories you used before.
After using it for a while you could find some files in your home directory which are starting with `.z.` and some numbers.
This are the files z where z records your directory usage and which are used to determine in which directory it should change.
After installing it you will first forget about it but when you rediscover it you would be able to switch to any directory you use frequently with just a few keystrokes.

Personally I use it pretty much, I have very few aliases in my shell configuration to switch directories and for all else I often use z. 
You should at least try it out ;)
