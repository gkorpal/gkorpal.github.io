---
layout: single
title:  "Creating ideal LaTeX editing setup"
header:
categories: 
  - Jekyll
tags:
  - edge case
---
Arch way of doing stuff.

The plan is to use [Vim](https://www.vim.org/) as the text-editor and [MuPDF](https://mupdf.com/) as the pdf-viewer since both can be accessed solely via keyboard, while keeping all the desired features from other LaTex editor like "live pdf preview" from GTK based [Gummi](https://github.com/alexandervdm/gummi) and "forward and backward search to switch between the sources and the PDF" from Qt based [TexMaker](https://www.xm1math.net/texmaker/).

We will need the following packages to begin with:

| Software Program | dnf Package |
|----------|----------|
|[TeX Live](https://docs.fedoraproject.org/en-US/neurofedora/latex/) | `texlive-scheme-full`|
|[Vim](https://fedoraproject.org/wiki/Vim) |`vim`|
| [MuPDF](https://mupdf.com/) | `mupdf`|
| [Inkscape](https://inkscape.org/) | `inkscape`|

If you want GUI version of Vim then can get gVim by installing the package `vim-X11`. For gVim you will have to [modify these steps](https://vi.stackexchange.com/questions/11484/) accordingly.

# Vim configuration

Once you finish learning basics using `vimtutor`, you are ready to start configuring Vim as per your requirements.

## .vimrc file creation and backup

To start Vim with all the favorite option settings and mappings, one writes them in what is called the `vimrc` file. The `vimrc` file can contain all the commands that you type after a colon. Vim executes the commands in this file when it starts up. Read [the documentation](http://vimdoc.sourceforge.net/htmldoc/usr_05.html) for more details. Note that Vim 8.0 onwards, if Vim is started normally and no user vimrc file is found, the `defaults.vim` script is loaded.  This will set 'compatible' off, switch on syntax highlighting and a few more things.  See this [reddit post](https://www.reddit.com/r/vim/comments/66vjm8/a_rant_on_defaultsvim_in_vim_8/) for a discussion about this. To disable loading of `defaults.vim` completely add `let skip_defaults_vim=1` to `/etc/vimrc` ([see this](https://wiki.archlinux.org/index.php/Vim#Configuration)). 

Since `vimrc` is something personal that evolves over times as per one's usage requirements, it's [not recommended to blindly copy](https://github.com/romainl/idiomatic-vimrc) it from the internet. I used [this example](https://vim.fandom.com/wiki/Example_vimrc) as reference for creating the following `~/.vimrc`

`````
set nocompatible          " get rid of Vi compatibility mode. 
filetype plugin indent on " filetype detection[ON] plugin[ON] indent[ON]
set t_Co=256              " enable 256-color mode.
syntax enable             " enable syntax highlighting (can also use syntax on).
colorscheme desert        " on a light terminal the default is peachpuff. on a dark terminal the default is ron.
set hidden                " allows you to re-use the same window without saving it first and also keep an undo history for all the files using the same window.
set number                " show line numbers
set ruler                 " Always show cursor position.
set laststatus=2          " always display the status line so that you can see the current mode, file name, file status, ruler, etc. 
filetype indent on        " activates indenting for files
set hlsearch              " highlight searched phrases.
set ignorecase            " Make searches case-insensitive.
set smartcase             " Make search case-sesitive when using capital letters
set autoindent            " auto-indent
set tabstop=4             " tab spacing
set softtabstop=4         " unify
set shiftwidth=4          " indent/outdent by 4 columns
set shiftround            " always indent/outdent to the nearest tabstop
set expandtab             " use spaces instead of tabs
set smarttab              " use tabs at the start of a line, spaces elsewhere
set nowrap                " don't wrap text
`````

## vimtex plugin installation and configuration

# Usage instructions


https://wikimatze.de/vimtex-the-perfect-tool-for-working-with-tex-and-vim/

https://jdhao.github.io/2019/03/26/nvim_latex_write_preview/

https://medium.com/rahasak/vim-as-my-latex-editor-f0c5d60c66fa

http://tomchaplin.xyz/portfolio/Vim-for-LaTeX/

https://www.dianacai.com/blog/2018/06/28/latex-vim-skim-setup/



