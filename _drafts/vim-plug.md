---
layout: post
title:  "Vim: Automatic management of Plugins"
published: true
categories: vim
---

This is a follow up of my previous [post]({% post_url 2017-11-19-Vim-Basic-Plugins %}). In that post, I introduced
my favorite plugins and manually installed them, using vim-pathogen to manage the plugins. In this post, I will use
the great [vim-plug](https://github.com/junegunn/vim-plug) to handle the whole process. The best thing of this tool
is that you won't need to perform almost any manual step

Check out my [.vimrc](https://raw.githubusercontent.com/germfue/germfue.github.com/master/dotfiles/.vimrc) file.

# Installation

I will assume you start with a clean `.vim` folder. I do not recommend to mix vim-plug and vim-pathogen, unless
you know what you are doing.

    curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

The only extra dependencies you will need, are flake8 and jedi:

    pip install flake8 jedi # or for Python3
    pip3 install flake8 jedi

# List your plugins

Add in your .vimrc file the list of plugins you want vim-plug to manage:

    " Specify a directory for plugins
    " - For Neovim: ~/.local/share/nvim/plugged
    " - Avoid using standard Vim directory names like 'plugin'
    call plug#begin('~/.vim/plugged')

    " Install NERDTree, for file explorer panel
    Plug 'scrooloose/nerdtree'

    " Style highlighting for Saltfiles
    Plug 'saltstack/salt-vim'

    " Fancy color schemes
    Plug 'altercation/vim-colors-solarized'
    Plug 'jnurmine/Zenburn'

    " Syntax highlighting
    Plug 'vim-syntastic/syntastic'

    " Auto-complete
    Plug 'davidhalter/jedi-vim'

    " Initialize plugin system
    call plug#end()

This will:
1. Configure vim-plug to manage the plugins in the folder `~/.vim/plugged`.
2. Define the plugins to install
3. Initialize the plugin system

# Install the modules

It is pretty simple, start vim and type the following command:

    :PlugInstall

If you want a more detailed introduction to vim-plug, I would recommend checking the
[README.md](https://github.com/junegunn/vim-plug) in the github repository. It contains all you need to manage your
plugins
