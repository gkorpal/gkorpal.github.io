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
  - inkscpae
  - geogrbra
  - vimtex
  - vim
  - vim plug
  - vimrc
---
In this post I have written down the steps one can follow to use the Terminal Emulator as a versatile LaTeX editor.

# Preparation

The plan is to use [Vim](https://www.vim.org/) as the text-editor and [MuPDF](https://mupdf.com/) as the pdf-viewer since both can be accessed solely via keyboard, while keeping all the desired features from other LaTex editor like "live pdf preview" and "compile using latexmk" from GTK based [Gummi](https://github.com/alexandervdm/gummi) and "forward and backward search to switch between the sources and the PDF" and "detailed compilation errors" from Qt based [TexMaker](https://www.xm1math.net/texmaker/).

We will need the following packages to begin with:

| Software Program | dnf Package |
|----------|----------|
|[TeX Live](https://docs.fedoraproject.org/en-US/neurofedora/latex/) | `texlive-scheme-full`|
|[Vim](https://fedoraproject.org/wiki/Vim) |`vim`|
|[Git](https://src.fedoraproject.org/rpms/git) | `git`|
| [MuPDF](https://mupdf.com/) | `mupdf`|
| [command-line X11 automation tool](https://manned.org/xdotool/95401223) | `xdotool`|
| [Mathplotlib](https://developer.fedoraproject.org/tech/languages/python/scipy.html) |`python3-matplotlib`|
| [Inkscape](https://inkscape.org/) | `inkscape`|

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

# Drawing graphs and diagrams using pdfLaTeX

We can always use simple mathematical programs like GeoGebra for 2D and 3D graphs and drawing programs like Google Drawing for diagrams. These graphs and diagrams can be exported as png or jpg (raster graphics) and then inserted in pdf using `graphicx` package. 

````
\usepackage{graphicx} %add images
\graphicspath{ {./figures/} } %images are kept in a folder under the directory of the main document.
\usepackage{subcaption} %to add multiple subfigures.
````
However, for better integration into the pdf document we should be using vector graphics and it can be done with the help of following programs/packages:

## Graphs

### pgfplots

For including 2D and 3D plots, we can use the `pgfplots` package. Read the [documentation](http://pgfplots.sourceforge.net/). First include the following in the preamble:

````
\usepackage{pgfplots} %draws function plots using pgf/tikz
\pgfplotsset{compat=1.16} %running latest version of pgfplots
\usepgfplotslibrary{external} %avoid recompiling unchanged graphs
\tikzexternalize[prefix=./figures/] %images will be stored in a folder under the working directory to avoid recompling unchanged files
````

For example, we can plot 3D surfaces by following methods:
`````
\begin{tikzpicture} %https://tex.stackexchange.com/a/359914/
\begin{axis}[title=$f^{-1}(-1)$: Hyperboloid of 1 sheet,axis equal]
\addplot3[surf,domain=0:360,y domain=-2:2] ({cosh(y)*cos(x)},{cosh(y)*sin(x)},{sinh(y)});
\end{axis}
\end{tikzpicture}
`````

![alt text](https://gkorpal.github.io/images/hy1.png)

`````
  \begin{tikzpicture}%https://tex.stackexchange.com/a/28775/
  \begin{axis}[title=$f^{-1}(0)$: Double cone, domain=0:5, y domain=0:2*pi,xmin=-10, xmax=10, ymin=-10, ymax=10, samples=20]
  \addplot3 [surf,z buffer=sort] ({x*cos(deg(y))}, {x*sin(deg(y))}, {x});
  \addplot3 [surf,z buffer=sort] ({x*cos(deg(y))}, {x*sin(deg(y))}, {-x});
  \end{axis}
  \end{tikzpicture}
`````

![alt text](https://gkorpal.github.io/images/cone.png)

The downside of this method is that it will increase the compliation time if `prefix` option is not used (since pdfLaTeX is limited to single CPU thread).  We can also use `contour gnuplot` and `\addplot gnuplot` to extend the built-in capabilities of `pgfplots` by means of `gnuplot`’s math library, although their use is optional.

### Matplotlib

Another way of including 2D and 3D plots is to use the Python library `Mathplotlib`. Read this [guide](https://problemsolvingwithpython.com/06-Plotting-with-Matplotlib/06.00-Introduction/). I will illustrate the steps involved by the following plotting the 2D vector field $X=-y\frac{\partial}{\partial x} + x\frac{\partial}{\partial y} and its flow lines:
1. Save and run the following Python scripts in the "figures" subfolder inside the folder containg the main LaTeX file ([source1](https://krajit.github.io/sympy/vectorFields/vectorFields.html), ([source2](https://www.sbillaudelle.de/2015/02/23/seamlessly-embedding-matplotlib-output-into-latex.html))):

````
import numpy as np
import matplotlib.pyplot as plt

#use quiver plot to plot the vector field
x,y = np.meshgrid(np.linspace(-5,5,10),np.linspace(-5,5,10))
u = -y
v = x
plt.quiver(x,y,u,v)

#save as pdf and pgf
plt.savefig('field.pdf')
plt.savefig('field.pgf')
````

````
import numpy as np
import matplotlib.pyplot as plt

#use stream plot to create the flow lines
x,y = np.meshgrid(np.linspace(-5,5,10),np.linspace(-5,5,10))
u = -y
v = x
plt.streamplot(x,y,u,v)

#save as pdf and pgf
plt.savefig('flow.pdf')
plt.savefig('flow.pgf')
````

2. Add the following lines in the preamble of the main LaTeX file:

`````
\usepackage{pgf}
\usepackage{import} %import images from different folder 
`````

3. Finally, to include these plots in the document, use:

````
\resizebox{0.75\textwidth}{!}{\import{./figures/}{field.pgf}}

\resizebox{0.75\textwidth}{!}{\import{./figures/}{flow.pgf}}
````

You can also use `figure` or `center` environment as per your needs.

4. We will get the following plots with proper font and resolution:

![alt text](https://gkorpal.github.io/images/field.png)

![alt text](https://gkorpal.github.io/images/flow.png)


Alternatively, you can insert the `pdf` file by following [this guide](https://ercanozturk.org/2017/12/16/python-matplotlib-plots-in-latex/).
 
<!--- ### SageMath  For number theory related stuff. http://people.cst.cmich.edu/chan1cj/gss/tikzsage_demo.pdf --->

## Diagrams

### PGF/TikZ

Apart from all these tools, one can directly use TikZ package to manually draw things like flowcharts. Read the [documentation](https://pgf-tikz.github.io/pgf/pgfmanual.pdf) for details. For example, we can add the following to the preamble:

`````
\usepackage{tikz}
\usetikzlibrary{shapes,arrows, chains, matrix, calc, trees, positioning, fit}
\usetikzlibrary{external}
\tikzexternalize[prefix=./figures/] %images will be stored in a folder under the working directory
`````

Then we can draw function mapping:

`````
\begin{tikzpicture}[line width=1pt,>=latex]
			\node (a1) {$\mathbb{Q}_p(\sqrt{u}) \ \bullet$};
			\node[below=of a1] (a2) {$\mathbb{Q}_p(\sqrt{-p})\ \bullet$} ;
			\node[below=of a2] (a3) {$\mathbb{Q}_p(\sqrt{-p\cdot u})\ \bullet$};

			\node[right=4cm of a1] (b1) {$ \bullet \ \mu_p$};
			\node[right=4cm of a2] (b2) {$ \bullet \ \lambda_p$};
			\node[right=4cm of a3] (b3) {$ \bullet \ \mu_p\lambda_p$};

			\node[shape=ellipse, draw, minimum size=3cm,fit={(a1) (a3)}] {};
			\node[shape=ellipse, draw, minimum size=3cm,fit={(b1) (b3)}] {};

			\node[below=1cm of a3] {$\mathcal{E}$};
			\node[below=1cm of b3] {$\mathcal{Q}$};

			\draw[->] (a1) -- (b1);
			\draw[->] (a2) -- (b2);
			\draw[->] (a3) -- (b3);
\end{tikzpicture}
`````

![alt text](https://gkorpal.github.io/images/function.png)

and flowcharts

`````
\begin{tikzpicture}[>=latex']
\node[left] at (0,0) (input) {$p$};
\node[block] at (4,0) (block) [text=white]{\textbf{Reciprocity Law}};
\node at (9,0) (output) {$\chi_\tau(\Frob_p)$};
\draw[very thick, ->] (input) -- (block);
\draw[very thick, ->] (block) -- (output);
\end{tikzpicture}
`````

![alt text](https://gkorpal.github.io/images/flow.png)

### tikz-cd

We can draw commutative diagrams using `tikz-cd` package. Read its [documentation](https://ctan.org/pkg/tikz-cd?lang=en) for details. Firstly you will have to add the following to the preamble:

````
\usepackage{tikz-cd}

%%homebrewcommands

\newcommand{\delbar}{\overline{\partial}}
\newcommand{\Om}{\Omega}
\newcommand{\mz}{\mathcal{Z}}

\DeclareMathOperator{\ceco}{\check{H}}
````

Then add the following code:

````
\[\begin{tikzcd}[column sep = 1.5em]
0\arrow{r} & \mz^{p,\ell}(M) \arrow[hookrightarrow]{r} & \Om^{p,\ell}(M) \arrow{r}{\delbar} & \mz^{p,\ell+1}(M) \arrow{r}{\Delta} & \ceco^1(M,\mz^{p,\ell}) \arrow{r} & 0 \arrow{r} & \ceco^1(M,\mz^{p,\ell+1}) \arrow{d}{\Delta}\\
& \cdots & 0\arrow{l} & \ceco^3(M,\mz^{p,\ell}) \arrow{l}& \ceco^2(M,\mz^{p,\ell+1})\arrow{l}[swap]{\Delta} & 0 \arrow{l} & \ceco^2(M,\mz^{p,\ell})\arrow{l}
\end{tikzcd}\]
````

to get

![alt text](https://gkorpal.github.io/images/exact.png)


### GeoGebra Classic

The easiest way to include simple 2D graphs and diagrams is to use GeoGebra, since it gives us the option of exporting the Graphics View as PGF/TikZ code. Installing [GeoGebra Classic 6](https://wiki.geogebra.org/en/Reference:GeoGebra_Installation) is a dependency hell ([ex1](https://ask.fedoraproject.org/t/dnf-reports-geogebra-gpg-key-not-found/3376) and [ex2](https://help.geogebra.org/topic/geogebra-classic-and-fedora-32)). Therefore, we will just use the online version: https://www.geogebra.org/classic For example, add the following to the preamble:

`````
\usepackage{pgf,tikz}
\usetikzlibrary{arrows}%you can see what extra packages are needed by going through the exported tex file
\usetikzlibrary{decorations.markings}
`````

Then draw the following diagram in GeoGebra

![alt text](https://gkorpal.github.io/images/geogebra.png)

And add the following corresponding code in the tex file:

`````
\begin{tikzpicture}[line cap=round,line join=round, x=0.7cm,y=0.7cm]
\draw[->,color=black] (-5,0) -- (10,0);
\draw[->,color=black] (0,-5) -- (0,5);
\clip(-5,-5) rectangle (10,5);
\draw [line width=1.6pt,domain=3.0:10.0] plot(\x,{(-0-0*\x)/8});
\draw [decoration={markings, mark=at position 0.125 with {\arrow{>}}},
        postaction={decorate}, line width=1.6pt] (0,0) circle (2.1cm);
\draw (3.09,0.70) node[anchor=north west] {$\delta$};
\begin{scriptsize}
\fill [color=black] (3,0) circle (2pt);
\end{scriptsize}
\end{tikzpicture}
`````

### Inkscape

The easiest way to include diagrams as vector graphics is by using Inkscape as follows:
1. Draw the desired diagram in Inkscape, and enclose mathematical symbols in `$...$`. If you don't know how to use Inkscape then just go to `Help > Tutorials > Inkscape: Basic` and you will be ready to use.
2. Create a folder called "pictures" inside the folder containg the main tex file and save the diagram as `svg` so that you can edit it in the future if needed. Then also save [PDF+LaTeX](https://wiki.inkscape.org/wiki/index.php/LaTeX) output to the same "pictures" folder: `File > Save As... > Select PDF from the drop-down menu > Click Save > Choose the following options`

![alt text](https://gkorpal.github.io/images/options.png)

You can also [use command-line](https://graphicdesign.stackexchange.com/a/56792) to achieve the same result:
````
inkscape mySVGinputFile.svg --export-area-drawing --batch-process --export-type=pdf --export-filename=output.pdf
````

3. Add the following code to the preamble of your main tex file ([source1](https://en.wikibooks.org/wiki/LaTeX/Importing_Graphics#Vector_graphics) and [source2](https://gkorpal.github.io/files/InkscapePDFLaTeX.pdf)):
`````
\usepackage{import} % it will enable us to access images without keeping them in the document's directory
\usepackage{calc} % enable usage of \svgscale
\usepackage{graphicx} % for inserting images
\usepackage{xcolor} % for adding colors
\usepackage{transparent} % enables usage of separate color stack for transparency
`````
4. Now we can add "image.svg" in one of the following ways ([source1](https://tex.stackexchange.com/questions/151232/) and [source2](https://tex.stackexchange.com/questions/46312/)):

````
\begin{figure}[h]
\centering
\resizebox{75mm}{!}{\import{./figures/}{image.pdf_tex}}
\caption{Your figure}
\label{figure:example}
\end{figure}


\begin{figure}[h]
 \centering
\def\svgwidth{0.75\columnwidth}                 %Using \def\svgwidth{desired width} instead of \resizebox will preserve the font size
\import{./figures/}{image.pdf_tex}
\caption{Your figure}
\label{figure:example}
\end{figure}


\begin{figure}[h]
\centering
\def\svgscale{0.75}
\import{./figures/}{image.pdf_tex}
\caption{Your figure}
\label{figure:example}
\end{figure}
````

You can also [write scripts](https://castel.dev/post/lecture-notes-2/) to make this process easier. The main advantage of Inkscape is that there's hardly any command or action that is impossible to do from keyboard. Linux users may not get the expected results with the key combinations starting with `Alt` key if the Window Manager catches those key events before they reach the inkscape application. One solution would be to change the WM's configuration accordingly.

<!--- ### Asymptote https://tex.stackexchange.com/questions/167164/inserting-graphics-into-asymptote-or-pgfplots --->
