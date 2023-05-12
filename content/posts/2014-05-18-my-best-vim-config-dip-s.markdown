---

layout: post
date: 2014-05-18
title: "my best vim config dip's"
published: true
tags: ["vim","config"]

---

Here are some of my favourite bindings in vim.

The first thing to do in .vimrc:

``` bash
 " Unmap the Arrow Keys \{\{\{
 no <down> <Nop>
 no <left> <Nop>
 no <right> <Nop>
 no <up> <Nop>
 ino <down> <Nop>
 ino <left> <Nop>
 ino <right> <Nop>
 ino <up> <Nop>
 vno <down> <Nop>
 vno <left> <Nop>
 vno <right> <Nop>
 vno <up> <Nop>
```
The following are my private favourites for now and evolving.

<!-- more -->
``` bash
 " Jekyll Blog Bindings  \{\{\{
 let g:jekyll_path = "$HOME/git/blog"
 " Jekyll Bundle mappings
 map <Leader>jn  :JekyllPost<CR>
 map <Leader>jl  :JekyllList<CR>
 map <Leader>jc  :JekyllCommit<CR>
 map <Leader>jp  :JekyllPublish<CR>

 " Quickly edit/reload the vimrc file
 nmap <silent> <leader>ev :e $MYVIMRC<CR>
 nmap <silent> <leader>sv :so $MYVIMRC<CR>

 " Paste Mode for pasting more Text at once (use in insert mode)
 set pastetoggle=<F2>

 " Use sane regexes.
 nnoremap / /\v
 vnoremap / /\v

 " Easier to type
 noremap H ^
 noremap L $
 vnoremap L g_

 " gi already moves to "last place you exited insert mode", so we'll map gI to
 " something similar: move to last change
 nnoremap gI `.

 " Move the cursor one displaying line on the screen not in the text.
 " useful with wrapped lines
 noremap j gj
 noremap k gk
 noremap gj j
 noremap gk k

 " Easy buffer navigation in split view's
 noremap <C-h> <C-w>h
 noremap <C-j> <C-w>j
 noremap <C-k> <C-w>k
 noremap <C-l> <C-w>l
```
