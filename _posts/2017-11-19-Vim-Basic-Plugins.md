---
layout: post
title:  "Vim: Basic Plugins"
published: true
categories: vim
---
I use [Vim](http://www.vim.org) as my default editor. The reasons for it are simple, I feel
comfortable with it and the simple interface let's me concentrate better on the task at hand.

In this post I will introduce the main plugins I use and how to manually set them up. Check out my
[vimrc](https://raw.githubusercontent.com/germfue/germfue.github.com/master/dotfiles/.vimrc-pathogen) file for completeness.

# Relative line numbers in visual mode
I got this idea from
[Jeff's Blog](http://jeffkreeftmeijer.com/2012/relative-line-numbers-in-vim-for-super-fast-movement) (Thanks Jeff!)
 Using relative line numbers in visual mode speeds up some typical operations like calculating how many rows should be
copied or deleted

    :set relativenumber
    autocmd InsertEnter * :set number norelativenumber
    autocmd InsertLeave * :set nonumber relativenumber 

# Mark the 120 characters limit

This is an easy one, I like to limit my code to 120 chars wide maximum

    if exists('+colorcolumn')
        set colorcolumn=120
    else
        au BufWinEnter * let w:m2=matchadd('ErrorMsg', '\%>120v.\+', -1)
    endif

# `runtimepath` management with vim-pathogen

Use [vim-pathogen](https://github.com/tpope/vim-pathogen) to manage the vim `runtimepath`:

    $ mkdir -p ~/.vim/autoload ~/.vim/bundle
    $ curl -LSso ~/.vim/autoload/pathogen.vim https://raw.githubusercontent.com/tpope/vim-pathogen/master/autoload/pathogen.vim

Add this to vimrc:

    execute pathogen#infect()

Now it is time we start loading some plugins.

# Filesystem tree with [NERD Tree](https://github.com/scrooloose/nerdtree)

This is one of my favorite plugins. You can easily interact with the files in project by using this file tree.

To use it, download bundle:

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

If you need help with the shortcuts, you can find the documentation
[here](https://github.com/scrooloose/nerdtree/blob/master/doc/NERD_tree.txt)

# [Salt-vim](https://github.com/saltstack/salt-vim)

I use [SaltStack](https://saltstack.com) to manage my servers. This plugin comes handy when editing the configuration
files.

Download bundle:

    $ git clone https://github.com/saltstack/salt-vim.git ~/.vim/bundle/salt-vim

Check that this is in .vimrc:

    syntax on
    set nocompatible
    filetype plugin indent on

# Colors

These 2 color schemes are my favorites :)

    git clone https://github.com/altercation/vim-colors-solarized.git ~/.vim/bundle/vim-colors-solarized
    " curl -LSso ~/.vim/autoload/pathogen.vim https://raw.githubusercontent.com/tpope/vim-pathogen/master/autoload/pathogen.vim
    git clone https://github.com/jnurmine/Zenburn.git ~/.vim/bundle/Zenburn

Check that this is in .vimrc:

    if has('gui_running')
        set background=dark
        colorscheme solarized
    else
        colorscheme zenburn
    endif

# Syntastic

If you use vim to edit code, this plugin will help you

    git clone https://github.com/vim-syntastic/syntastic.git ~/.vim/bundle/syntastic


Check that this is in .vimrc:

    set statusline+=%#warningmsg#
    set statusline+=%{SyntasticStatuslineFlag()}
    set statusline+=%*

    let g:syntastic_always_populate_loc_list = 0
    let g:syntastic_auto_loc_list = 0
    let g:syntastic_check_on_open = 1
    let g:syntastic_check_on_wq = 0
    let g:syntastic_python_python_exe = 'python3'
    let g:syntastic_python_checkers=['flake8']
    let g:syntastic_python_flake8_args='--max-line-length=120'

You will need to install flake8 in your system:

    pip install flake8 # or for Python3
    pip3 install flake8

# Auto-complete with Jedi

Isn't it easier to edit when you have auto-complete?

    git clone https://github.com/davidhalter/jedi-vim.git ~/.vim/bundle/jedi-vim

    cd ~/.vim/bundle/jedi-vim
    virtualenv .
    source bin/activate
    pip install jedi
    rmdir jedi
    ln -s lib64/python2.7/site-packages/jedi jedi

# Ready to go
With these basic plugins I handle most of the tasks my every day's activities require. I hope they help you too!
