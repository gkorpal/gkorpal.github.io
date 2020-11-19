---
title: 'Using Terminal Emulator as LaTeX editor'
date: 2020-08-31
permalink: /posts/2020/08/latex-vim-mupdf/
tags:
  - pc
  - latex  
  - linux
  - xfce4-terminal
  - fedora
  - terminal-emulator
  - vimtex
  - vim
  - vim plug
  - vimrc
---
In this post I have written down the steps one can follow to use the Terminal Emulator as a versatile LaTeX editor. A good reference for learning LaTeX is "[The not so Short Introduction to LaTeX](https://ctan.org/tex-archive/info/lshort/english/)."

# Preparation

The plan is to use [Vim](https://www.vim.org/) as the text-editor and [MuPDF](https://mupdf.com/) as the pdf-viewer since both can be accessed solely via keyboard, while keeping all the desired features from other LaTex editor like "live pdf preview" and "compile using latexmk" from GTK based [Gummi](https://github.com/alexandervdm/gummi) and "forward and backward search to switch between the sources and the PDF" and "detailed compilation errors" from Qt based [TexMaker](https://www.xm1math.net/texmaker/).

We will need the following packages to begin with:

| Software Program | dnf Package |
|----------|----------|
|[TeX Live](https://docs.fedoraproject.org/en-US/neurofedora/latex/) | `texlive-scheme-full`|
|[Vim](https://fedoraproject.org/wiki/Vim) |`vim`|
|[Git](https://src.fedoraproject.org/rpms/git) | `git`|
|[MuPDF](https://mupdf.com/) | `mupdf`|
|[command-line X11 automation tool](https://manned.org/xdotool/95401223) | `xdotool`|

If you want GUI version of Vim then can get gVim by installing the package `vim-X11`. For gVim you will have to [modify these steps](https://vi.stackexchange.com/questions/11484/) accordingly.

# Vim configuration

Once you finish learning basics using `vimtutor`, you are ready to start configuring Vim as per your requirements.

## .vimrc file creation

To start Vim with all the favorite option settings and mappings, one writes them in what is called the `vimrc` file. The `vimrc` file can contain all the commands that you type after a colon. Vim executes the commands in this file when it starts up. Read [the documentation](http://vimdoc.sourceforge.net/htmldoc/usr_05.html) for more details. Note that Vim 8.0 onwards, if Vim is started normally and no user vimrc file is found, the `defaults.vim` script is loaded.  This will set 'compatible' off, switch on syntax highlighting and a few more things.  See this [reddit post](https://www.reddit.com/r/vim/comments/66vjm8/a_rant_on_defaultsvim_in_vim_8/) for a discussion about this. To disable loading of `defaults.vim` completely add `let skip_defaults_vim=1` to `/etc/vimrc` ([see this](https://wiki.archlinux.org/index.php/Vim#Configuration)). 

Since `vimrc` is something personal that evolves over times as per one's usage requirements, it's [not recommended to blindly copy](https://github.com/romainl/idiomatic-vimrc) it from the internet. I used [this example](https://vim.fandom.com/wiki/Example_vimrc) as reference for creating the following `~/.vimrc`

`````
set nocompatible               " get rid of Vi compatibility mode. 
filetype plugin indent on      " filetype detection[ON] plugin[ON] auto-indent[ON] depending on filetype
set t_Co=256                   " enable 256-color mode.
syntax enable                  " enable syntax highlighting (can also use syntax on).
colorscheme morning            " I am using it with solarized (dark) color pallet in xfce4-terminal.
set hidden                     " allows you to re-use the same window without saving it first and keep an undo history for all the files using the same window.
set number                     " show line numbers to the left
set ruler                      " Always show cursor position.
set laststatus=2               " always display the status line so that you can see the current mode, file name, file status, ruler, etc. 
filetype indent on             " activates indenting for files
set hlsearch                   " highlight searched phrases.
set ignorecase                 " Make searches case-insensitive.
set smartcase                  " Make search case-sesitive when using capital letters
set autoindent                 " When opening a new line and no filetype-specific indenting is enabled, keep " the same indent as the line you're currently on.
set backspace=indent,eol,start " Allow backspacing over autoindent, line breaks and start of insert action
set tabstop=8                  " sets tab stops to 8 characters wide
set softtabstop=4              " makes the Tab key intent by 4 spaces
set shiftwidth=4               " width of autointents set to 4 spaces
set expandtab                  " converts tabs to white space
set mouse=a                    " Enable use of the mouse for all modes
set wrap linebreak nolist      " Soft wrapping text. To move the cursor up and down within wrapped line use the commands gk and gj.
`````

You can [use this guide](http://blog.smalleycreative.com/tutorials/using-git-and-github-to-manage-your-dotfiles/) to create a backup of your `vimrc` file using GitHub so that you can easily configure Vim on any other computer. It will boil down to writing a [backup script](https://dev.to/jeffshomali/how-to-backup-sync-all-of-your-dotfiles-with-github-e1c).

## vimtex plugin installation and configuration
 
You can install `vimtex` manually or using a plugin manager ([see this guide](https://linuxhint.com/vim_install_plugins/)). We will use the [vim-plug](https://github.com/junegunn/vim-plug) plugin manager to install `vimtex`. Firstly, we will download [plug.vim](https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim) and put it in the `~/.vim/autoload` directory using following code:

`````
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
`````
Next we will enable `vimtex` by  adding the following section to the `~/.vimrc` file:

`````
call plug#begin('~/.vim/plugged')  " Specify the directory ~/.vim/plugged for plugins. Avoid using standard Vim directory names like ~/.vim/plugin
Plug 'lervag/vimtex'               " Shorthand notation for fetching the vimtex plugin from https://github.com/lervag/vimtex
call plug#end()                    " To update &runtimepath and initialize plugin system
`````

Once the vimrc is properly configured, restart Vim or reload the vimrc file (make sure that `git` is installed for this to work). Finally, run the `:PlugInstall` command to start the installation of `vimtex` plugin. Vim-plug will download all the packages directly from GitHub and put them into the `~/.vim/plugged` directory and load them whenever Vim is loaded. To update plugins use `:PlugUpdate` command and to remove them use `:PlugClean` command. Also, to update vim-plug itself, use `:PlugUpgrade` command.

Now we will set it up following the [official documentation](https://github.com/lervag/vimtex/blob/master/doc/vimtex.txt) of `vimtex`, and adding the following to `~/.vimrc`:

`````
let g:tex_flavor = 'latex'           " Vim ships with some support for plain TeX, ConTeXt, and LaTeX files. This means that the `.tex` extension is ambiguous. Vimtex is only activated for LaTeX files with 'filetype' set to `tex`.
let g:vimtex_view_method = 'mupdf'   "  Set the pdf viewer. MuPDF supports forward and backward search via xdotool. For backward search use :VimtexRSearch command. Forward search will only take you to the correct page.  Backward search will take you to the line in Vim that corresponds to the first line of the current page in MuPDF.
let g:vimtex_compiler_latexmk= {'options' : ['-pdf', '-shell-escape', '-verbose', '-file-line-error', '-synctex=1', '-interaction=nonstopmode',],} " we need to enable -shell-escape to be able to use externalization library for avioiding recompiling unchanged diagrams/graphs created using tikz/pgfplots
`````
Note that by default the following desired options are already there:
* latexmk is the compiler which does compilation as soon as you save the file (continous compilation, better than live preview)
* auto-completion is enabled, 
* BibTex is used for bib files, 
* fold types are enabled, 
* intentation in both tex and bib are enabled, 
* vimtex will open the pdf viewer automatically after compilation
* forward search is enabled, i.e. it will perform a forward search to the current cursor position when the first invocation of the pdf viewer happens. It uses SyncTex and requires `xdotool` to work with MuPDF.

You can further customize by adding snippets as demonstrated in various blog posts ([ex1](https://castel.dev/post/lecture-notes-1/), [ex2](https://www.dianacai.com/blog/2018/06/28/latex-vim-skim-setup/), [ex3](http://tomchaplin.xyz/portfolio/Vim-for-LaTeX/) and [ex4](https://jdhao.github.io/2019/03/26/nvim_latex_write_preview/)). 

# Usage instructions

Following are the useful key mappings for the various vimtex commands:

| Key mapping | Vimtex command  (normal mode)| Output |
|----------|----------|----------|
| `\\ll` | :VimtexCompile | Run latexmk compiler in continuous mode which complies the saved tex file and shows the pdf. This command works as a compiler toggle.|
| `\\lv` | :VimtexView  |  View pdf for current project and perform forward search if available.|
| `\\lr` | :VimtexRSearch |  Do reverse search (only available for MuPDF viewer with `xdotool` installed).|
| `\\le` | :VimtexErrors  | Open `quickfix` window if there are errors or warnings. Press `:ccl` to close it. |
| `\\lk` | :VimtexStop    | Stop compilation for the current project.|
| `\\li` | :VimtexInfo    | Show information that is stored by vimtex about the current LaTeX project. Press `q` to exit|
| `\\lt` | :VimtexTocOpen    | Open table of contents. Press `q` to exit |
| `\\lg` | :VimtexStatus     |     Show compilation status for current project.|
| `\\ls` | :VimtexToggleMain | If you are working with multiple tex files may want to change the main file for the project |

We have many other shorthand keymaps like:

| Key mapping | Vim mode| Output |
|-------------|---------|--------|
| `]]`  | insert | Closes the current environment or delimiter, i.e adds `\end{foo}` for the corresponding `\begin{foo}`|
| `]]`  | normal | Go to next end of a section. |
| `][`  | normal | Go to next beginning of a section. |
| `[]`  | normal | Go to previous end of a section. |
| `[[`  | normal | Go to previous beginning of a section.|
| `]m`  | normal | Go to next start of an environment `\begin`. |
| `]M`  | normal | Go to next end of an environment `\end`. |
| `[m`  | normal | Go to previous start of an environment `\begin`.|
| `[M`  | normal | Go to previous end of an environment `\end`.|
| `dse` | normal | Delete the surrounding environment, i.e delete both `\begin{foo}` and `\end{foo}`. |
| `dsc` | normal | Delete surrounding command like `\begin{}` deleted from `\begin{foo}`|
| `cse` | normal | Change the surrounding environment, i.e change both `\begin{foo}` and `\end{foo}` to `\begin{too}` and `\end{too}` |
| `csc` | normal | Change surrounding command like `\begin{foo}` changed to `\end{foo}`|


Note that vimtex supports most multi-file documents. The main method uses a recursive search algorithm that should find the main LaTeX file in most cases. Read [the documentation](https://github.com/lervag/vimtex/blob/master/doc/vimtex.txt) for more details. 
