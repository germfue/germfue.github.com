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

# Python-mode

    git clone https://github.com/klen/python-mode.git ~/.vim/bundle/python-mode

Check that this is in .vimrc:

    filetype off

    execute pathogen#infect()
    execute pathogen#helptags()

    filetype plugin indent on
    syntax on
    
    " Python-mode
    " Activate rope
    " Keys:
    " K             Show python docs
    " <Ctrl-Space>  Rope autocomplete
    " <Ctrl-c>g     Rope goto definition
    " <Ctrl-c>d     Rope show documentation
    " <Ctrl-c>f     Rope find occurrences
    " <Leader>b     Set, unset breakpoint (g:pymode_breakpoint enabled)
    " [[            Jump on previous class or function (normal, visual, operator modes)
    " ]]            Jump on next class or function (normal, visual, operator modes)
    " [M            Jump on previous class or method (normal, visual, operator modes)
    " ]M            Jump on next class or method (normal, visual, operator modes)
    let g:pymode_rope = 1
    
    " Documentation
    let g:pymode_doc = 1
    let g:pymode_doc_key = 'K'
    
    "Linting
    let g:pymode_lint = 1
    let g:pymode_lint_checker = "pyflakes,pep8"
    " Auto check on save
    let g:pymode_lint_write = 1
    
    " Support virtualenv
    let g:pymode_virtualenv = 1
    
    " Enable breakpoints plugin
    let g:pymode_breakpoint = 1
    let g:pymode_breakpoint_bind = '<leader>b'
    
    " syntax highlighting
    let g:pymode_syntax = 1
    let g:pymode_syntax_all = 1
    let g:pymode_syntax_indent_errors = g:pymode_syntax_all
    let g:pymode_syntax_space_errors = g:pymode_syntax_all
    
    " Don't autofold code
    let g:pymode_folding = 0
