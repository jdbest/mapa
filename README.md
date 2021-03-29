# Git Markdown example

This is a simple example of using R Markdown documents to create APA-formatted documents with LaTeX compiling them into PDFs. You will need to install a version of LaTeX to compile; some suggestions are included [here](https://bookdown.org/yihui/rmarkdown-cookbook/install-latex.html), but if they do not work, you may want to install [MacTeX](http://tug.org/mactex/) for Macs or [MiKTeX](https://miktex.org/) for PCs. Of course, the Rmd document can also be compiled (knit) as an HTML file if you do not want to install a TeX distribution, but it will not follow APA style.

You will have to compile your references in a bibliography. Most folks recommend using Zotero, as do I; you'll need to output your references to a .bib file. Document/article titles will follow the capitalization you've got---use APA style yourself! (The most recent versions of R Markdown can also [help add your references](https://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html), including just from a DOI link.)

Some packages (e.g., {[papaja](https://github.com/crsh/papaja)}; Aust & Barth, 2020) will create APA-draft manuscripts, but may introduce extra details beyond the basic style. The style I lay out here will simply create a document using APA formatting of references. 

# Getting started

You will need to download the `apa.csl` and `template.tex` documents into a directory where your Rmd file lives. Open (or create) your R Markdown document.

Your document will automatically include some YAML headers:

```
---
title: "Your title"
author: "Your name"
date: "3/29/2021"
output: pdf_document
---
```

You can keep the title and date, but you will need to update the others headers to include some of the following YAML headers in your R Markdown document. In particular, you must include the `doctype`, the full set of `output` parameters (`output: pdf_document: template: "template.tex"`), and the `bibliography` and `csl` lines. The others, including `shorttitle` and `leftheader`, `authors_note`, and so forth, are implemented in APA style documents. 

```
---
doctype: jou # this can be stu, jou, doc, or man -- try each out!
title: "Your title"
author: 
  - name: "Your name"
    affiliation_number: 1
    affiliation: "Your affiliation"
shorttitle: "APA short title"
leftheader: "Authors' last names (for jou doctype only)"
authors_note: |
  This is an author's note; you could remove it if not desired. 
abstract: "Your article's abstract"
keywords: "example, keywords"
date: "`r format(Sys.time(), '%B %d, %Y')`" # This print's today's date; put in a specific date if you prefer
output: 
  pdf_document:
    template: "template.tex"
bibliography: example.bib # update to be your .bib file!
csl: apa.csl
---
```

# Example

On github you'll find an example of 


# More information

The reader hoping for more information should review some of the following books:

* [R Markdown Cookbook](https://bookdown.org/yihui/rmarkdown-cookbook/) by Yihui Xie, Christophe Dervieux, & Emily Riederer
* [bookdown: Authoring Books and Technical Documents with R Markdown](https://bookdown.org/yihui/bookdown/) by Yihui Xie