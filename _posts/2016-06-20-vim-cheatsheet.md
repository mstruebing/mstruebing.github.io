---
layout: post
section-type: post
title: vim cheatsheet
category: cheatsheet
tags: [ 'editor', 'unix', 'linux', 'terminal', 'programming' ]
---

After my [vim is nice post](/tech/2016/06/15/vim-is-nice) I decided to write a
quick cheatsheet for stuff I need the most
You can see some of my configuration in my dotfiles:
[.vimrc](https://github.com/mstruebing/dotfiles/blob/master/.vimrc) and
[my filetype plugins](https://github.com/mstruebing/dotfiles/tree/master/.vim/ftplugin)

This post will be updated if I find new useful things to do with vim

```
h - left
j - down
k - up
l - right

d - delete
r - replace
c - change (delete and go into insert mode)
y - yank(copy)
p - paste
x - delete char at cursor

w - word
e - end of word
b - backwards

a - append
A - append at end of line

$  - end of line
^ - beginning of line

i - insert mode
v - visual mode

:! - cli command

nnoremap - normale mode map
inoremap - insert mode map
vnoremap - visual mode map

:s - sed

:r <FILE> - read a file contents into the current buffer

:qa - quit all
:wqa - save and quit all
:x - save and quit
ZZ - save and quit

:e - explore (open files)
:vsplit file - open file in vertical split
:split file - open file in horizontal split
<CTRL> + w + w - change active buffer

:set spell spelllang=en_us - activate spelling check in english
]s - next wrong spelled word
[s - previous wrong spelled word
zg - add word to spellfile
z= - gives alternatives

-- mixed stuff --
xp - swap characters (delete and paste)
5j - move 5 lines down
dd - delete whole line
yy - yank whole line
cc - change whole line
ct) - change to )
dw - delete word
cw - change word
nnoremap <buffer> <F12> :w<CR>:!gcc -Wall %<CR> - sets F12 in current buffer(useful for filetype plugin) to save file and compile it with gcc
inoremap ( ()<left>
<CTRL> + n - auto suggestion even over various buffers
<CTRL> + R + "- paste in insert mode
:s#^#//# - place // at the beginning of the current/visual selected line you could and should also map that to a key
```
