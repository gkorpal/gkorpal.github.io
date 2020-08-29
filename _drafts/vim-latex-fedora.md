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
|----------|----------|---------|
|[TeX Live](https://docs.fedoraproject.org/en-US/neurofedora/latex/) | `texlive-scheme-full`|
|[Vim](https://fedoraproject.org/wiki/Vim) |`vim`|
| [MuPDF](https://mupdf.com/) | `mupdf`|
| [Inkscape](https://inkscape.org/) | `inkscape`|

If you want GUI version of Vim then can get gVim by installing the package `vim-X11`. For gVim you will have to [modify these steps](https://vi.stackexchange.com/questions/11484/) accordingly.

## .vimrc file creation and backup

## vimtex plugin installation and configuration


## Inkscape usage for drawing diagrams




https://wikimatze.de/vimtex-the-perfect-tool-for-working-with-tex-and-vim/

https://jdhao.github.io/2019/03/26/nvim_latex_write_preview/

https://medium.com/rahasak/vim-as-my-latex-editor-f0c5d60c66fa

http://tomchaplin.xyz/portfolio/Vim-for-LaTeX/

https://www.dianacai.com/blog/2018/06/28/latex-vim-skim-setup/



