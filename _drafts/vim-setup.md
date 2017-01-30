---
layout: post
title:  "Development on Vim"
published: true
categories: development ide vim
---
I use [Vim](http://www.vim.org) on a daily basis as a development environment. The reasons for it are simple, I feel comfortable with it and the simple interface let's me concentrate better on the task at hand.

Here you will find the instructions I followed for the setup and my [vimrc](https://raw.githubusercontent.com/germfue/dotfiles/master/.vimrc) file for completeness.

# `runtimepath` management with vim-pathogen

Use [vim-pathogen](https://github.com/tpope/vim-pathogen) to manage the vim `runtimepath`:

    $ mkdir -p ~/.vim/autoload ~/.vim/bundle
    $ curl -LSso ~/.vim/autoload/pathogen.vim https://raw.githubusercontent.com/tpope/vim-pathogen/master/autoload/pathogen.vim

Add this to vimrc:

    execute pathogen#infect()

# Filesystem tree with [NERD Tree](https://github.com/scrooloose/nerdtree)

Download bundle:

    $ git clone https://github.com/scrooloose/nerdtree.git ~/.vim/bundle/nerdtree

Add this to vimrc for default configuration:

    " This is the first line
    autocmd StdinReadPre * let s:std_in=1

    " Open NERD Tree automatically when vim starts up on opening a directory
    " Do not remove this line, or NERD Tree will be opened twice
    autocmd VimEnter * if argc() == 1 && isdirectory(argv()[0]) && !exists("s:std_in") | exe 'NERDTree' argv()[0] | wincmd p | ene | endif

    " Open NERD Tree automatically when vim starts up on opening a file
    autocmd VimEnter * NERDTree
    " ... and focus on the editing window
    :au VimEnter * if argc() > 0 | wincmd p | endif

    " Close vim if NERD Tree is the only window open
    autocmd bufenter * if (winnr("$") == 1 && exists("b:NERDTree") && b:NERDTree.isTabTree()) | q | endif

# Salt-vim (https://github.com/saltstack/salt-vim)

Download bundle:

    $ git clone https://github.com/saltstack/salt-vim.git ~/.vim/bundle/salt-vim

Check that this is in .vimrc:

    syntax on
    set nocompatible
    filetype plugin indent on

