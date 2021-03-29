# Git Markdown example

This is a simple example of using R Markdown documents to create APA-formatted documents with LaTeX compiling them into PDFs. You will need to install a version of LaTeX to compile; some suggestions are included [here](https://bookdown.org/yihui/rmarkdown-cookbook/install-latex.html), but if they do not work, you may want to install [MacTeX](http://tug.org/mactex/) for Macs or [MiKTeX](https://miktex.org/) for PCs. Of course, the Rmd document can also be compiled (knit) as an HTML file if you do not want to install a TeX distribution, but it will not follow APA style.

You will have to compile your references in a bibliography. Most folks recommend using Zotero, as do I; you'll need to output your references to a .bib file. 

Some packages (e.g., {[papaja](https://github.com/crsh/papaja)}) will create APA-draft manuscripts, but may introduce extra details beyond the basic style. The style I lay out here will simply create a document using APA formatting of references. 

# Installation

You will need to download the `apa.csl` and `template.tex` documents into a directory where your Rmd file lives. Include the following YAML headers in your R Markdown document:

```
this
```

# More information

The reader hoping for more information should review some of the following books:

* [R Markdown Cookbook](https://bookdown.org/yihui/rmarkdown-cookbook/) by Yihui Xie, Christophe Dervieux, & Emily Riederer
* [bookdown: Authoring Books and Technical Documents with R Markdown](https://bookdown.org/yihui/bookdown/) by Yihui Xie