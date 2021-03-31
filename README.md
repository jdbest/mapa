# Git Markdown example

(This text replicates the text in example.* included above. Where possible, links to documents on github are included here, but plots are not.)

This is a simple example of using R Markdown documents to create APA-formatted documents with LaTeX compiling them into PDFs. You will need to install a version of LaTeX to compile; if you do not have one, you'll find information about using [TinyTeX](https://yihui.org/tinytex/) (Xie, 2019) for this purpose [here](https://bookdown.org/yihui/rmarkdown-cookbook/install-latex.html). Before installing TinyTeX, I recommend ensuring that you have up-to-date versions of [RStudio](https://www.rstudio.com/products/rstudio/download/), [R](https://cran.r-project.org/), and (if you're using a Windows computer) [Rtools](https://cran.r-project.org/bin/windows/Rtools/). 

Then, install the {_tinytex_} package and use it to install TinyTeX: 

```
install.packages('tinytex')
tinytex::install_tinytex()
```

After installation, you may need to install the `apa7` LaTeX package (Weiss, 2021) with the command `tinytex::tlmgr_install("apa7")` -- I have tested this on a Windows computer (RStudio version 1.4.1106; R Version 4.0.5) and seen that it will install the relevant package; however, knitting the document for the first time will also result in the installation of other missing packages. (For more information, [see here](https://bookdown.org/yihui/rmarkdown-cookbook/install-latex-pkgs.html).)

If TinyTeX does not work for you or if you intend to use LaTeX beyond for this work, you may want to install [MacTeX](http://tug.org/mactex/) for Macs or [MiKTeX](https://miktex.org/) for PCs. (These are large installations---thus the point of a "tiny" version.)

You will also have to compile your references in a bibliography. Most folks recommend using Zotero, as do I (manually maintaining references can be frustrating); you'll need to output your references to a .bib file. Document/article titles will follow the capitalization you've got---use APA style yourself! (The most recent versions of R Markdown can also [help add your references](https://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html), including just from a DOI link.)

Some packages (e.g., {_[papaja](https://github.com/crsh/papaja)_}; Aust & Barth, 2020) will create APA-draft manuscripts, but may introduce extra details beyond the basic style. The style I lay out here will simply create a document using APA formatting of references. 

# Why would I want to use this template?

You might think it's fun to lay your document out in R Markdown! You might also want to report the results of tests directly into your document, or include graphs. You might also be procrastinating finishing a paper, and that's fine, too. 

I make no promises that this document will help you achieve "perfect" APA style---you'll need to double-check everything, especially your references. (In particular, if you are a student, make sure that this style conforms to any course/assignment requirements.)

# Getting started

You will need to download the [`apa.csl`](https://github.com/jdbest/Git_Markdown_example/blob/master/apa.csl) and [`template.tex`](https://github.com/jdbest/Git_Markdown_example/blob/master/template.tex) documents into a directory where your Rmd file lives. Open (or create) your R Markdown document.

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
doctype: man # this can be stu, jou, doc, or man
title: "Your title"
author: 
  - name: "Your name"
    affiliation_number: 1
affiliations: "Your affiliation"
shorttitle: "APA short title"
authors_note: |
  This is an author's note; 
  you could remove it if not desired. 
abstract: "Your article's abstract"
keywords: "example, keywords"
date: "3/29/21"
output: 
  pdf_document:
    template: "template.tex"
bibliography: example.bib # update to your .bib file!
csl: apa.csl
---
```

A minimal example is included ([minimal_example.Rmd](https://github.com/jdbest/Git_Markdown_example/blob/master/minimal_example.Rmd) and [minimal_example.pdf](https://github.com/jdbest/Git_Markdown_example/blob/master/minimal_example.pdf)) with these headers; feel free to download it and adapt. Without any changes, knitting it in R Markdown will make the PDF you can see here, so long as you have installed LaTeX---and downloaded the template.tex and apa.csl files into the same directory. (How to knit? Hit the "Knit" button in R Studio with the Rmd file open, or hit CMD+Shift+K / Ctrl+Shift+K.)

If you look at [example.Rmd](https://github.com/jdbest/Git_Markdown_example/blob/master/example.Rmd), you'll see how to include multiple authors with differing affiliations. List each author separately. Including `affiliation_number` will provide a superscript number after that name, which then anticipates a subsequent item under `affiliations`. (With only one affiliation, you do not need to include any `affiliation_number`. For each `affiliation_number`, there should be an affiliation listed as `affiliations`.) If an author has multiple affiliations, simply enclose the numbers in quotation marks, as below, separated with a comma: "2,3".


```
author: 
  - name: "First Author"
    affiliation_number: 1
  - name: "Second Author"
    affiliation_number: 2
  - name: "Third Author"
    affiliation_number: "2,3"
  - name: "Fourth Author"
    affiliation_number: 1
affiliations:
  - "First Institution"
  - "Other Institution"
  - "Yet another Institution"
```

As described below, there are some additional headers you may include:

* `leftheader`: The authors' last names (for `jou` doctype only)
* For the `stu` doctype, info about the course: `professor`, `course`, and `duedate`

There are additional YAML headers often used for different documents in R Markdown, many of which may work here. 

# Document types

The **{apa7}** document class in LaTeX accepts four document types---they're mentioned briefly above under `doctype`; you can try each out. Here's what they are:

* _jou_: journal style; intended to mimic what a journal looks like (two columns, etc). This will look weird with the minimal_example file---it looks better with a longer file -- this will also make use of the YAML `leftheader` and `shorttitle`, which will alternate page headers.
* _doc_: a one-column PDF output with APA style (including abstract, etc); it will try to be the "easiest to read"
* _man_: APA's suggestion for how to submit documents to a journal---what many instructors ask for in college course, with double-spacing and so forth
* _stu_: student papers---includes YAML headers `professor`, `course`, and `duedate`; otherwise much like `man`

I've created versions of this Rmd file with each document style, so you can see what they might look like: [example_jou.pdf](https://github.com/jdbest/Git_Markdown_example/blob/master/example_jou.pdf), [example_doc.pdf](https://github.com/jdbest/Git_Markdown_example/blob/master/example_doc.pdf), [example_man.pdf](https://github.com/jdbest/Git_Markdown_example/blob/master/example_man.pdf), & [example_stu.pdf](https://github.com/jdbest/Git_Markdown_example/blob/master/example_stu.pdf).

# Writing in an R Markdown file

Now that you have a working R Markdown file, you've chosen a document type, and you've updated it with your paper title and name, etc., your focus is on writing the document! 

If you've ever looked into LaTeX document writing, this is more simple. There are three major things to keep in mind:

1. Use \# to start a section, \## to start a subsection, etc.
2. Use square brackets [] to enclose references, e.g., `[@referencekey]`, where you precede a key with the @ symbol. The "reference key" is the way it will be referred in your .bib file---in [example.bib](https://github.com/jdbest/Git_Markdown_example/blob/master/example.bib), for example, you'll see that it's the first word of each entry. For more info on citations, [see here](https://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html#citations).

Most other formatting will be done for you. If you want to learn things about formatting in R Markdown, there are a variety of [cheatsheets](https://rmarkdown.rstudio.com/lesson-15.html) available; you can refer to the example.Rmd document here to learn about links, lists, _italics_ or **bold-face text**, etc.

# Including plots

As above, you can refer to the R Markdown cheatsheets to learn how to include pre-existing images. If you'd like to include *plots*, it's as easy as including a code chunk and using R code to create the figure (this uses the {_palmerpenguins_} and {_ggplot2_} packages by Horst et al. [2020] and Wickham [2016], respectively, and code from the first.) Including `echo=FALSE, warning=FALSE` means that the plot is printed but the code is not. If `echo` were TRUE, the code would also be printed. 

R Markdown and LaTeX will try their best to fit the plot into the space allotted to it; you can play around with size by specifying an `out.width` in percentages or inches. You may read about more options [here](https://bookdown.org/yihui/rmarkdown/pdf-document.html#figure-options-1), but note that full-page figures may be difficult when `doctype` is set as `jou`. (But see more in the examples.)

I don't include figures in this readme file---view the Rmd or PDF files.

There are many great R packages for writing LaTeX tables in R; you can see more in [tables_ex.Rmd](https://github.com/jdbest/Git_Markdown_example/blob/master/tables_ex.Rmd) and the associated [PDF](https://github.com/jdbest/Git_Markdown_example/blob/master/tables_ex.pdf). 

# More information

The reader hoping for more information should review some of the following books:

* [R Markdown: The Definitive Guide](https://bookdown.org/yihui/rmarkdown/) by Yihui Xie, J. J. Allaire, Garrett Grolemund
* [R Markdown Cookbook](https://bookdown.org/yihui/rmarkdown-cookbook/) by Yihui Xie, Christophe Dervieux, & Emily Riederer
* [bookdown: Authoring Books and Technical Documents with R Markdown](https://bookdown.org/yihui/bookdown/) by Yihui Xie
