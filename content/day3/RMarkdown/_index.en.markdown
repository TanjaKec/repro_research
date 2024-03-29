---
date: "2016-04-09T16:50:16+02:00"
title: RMarkdown
output: 
  learnr::tutorial
weight: 1
---
### Reproducible Research?! What is it? 🤷️

- Have you ever reproduced someone else's research analysis?

- How about reproducing your own old work? What tools did you use? 

- Do you know how to reproduce your collaborator's work? Was it hard or easy?

  - How would you go about extending the analysis further?

  - If you notice a data error how easy would it be to re-create the analysis?

  - What if your collaborator is no longer available? 


### What is R Markdown?

- [An authoring framework for data science](https://rmarkdown.rstudio.com/lesson-1.html)

- [A document format (.Rmd)](https://bookdown.org/yihui/rmarkdown/)

- [An R package named rmarkdown](https://rmarkdown.rstudio.com/docs/)

- [A file format for making dynamic documents with R](https://rmarkdown.rstudio.com/articles_intro.html)

- [A tool for integrating prose, code, and results](https://r4ds.had.co.nz/communicate-intro.html)

- [A computational document](http://radar.oreilly.com/2011/07/wolframs-computational-documen.html)

- Wizardry

[Alison Hill](https://alison.rbind.io) from [R Markdown Anatomy](https://rmd4medicine.netlify.com/slides/01-rmd-anatomy.html#1)

R Markdown can help generate: 

- HTML documents
- Notebooks in which you’ve run code chunks individually
- PDFs that you can print out to follow along physically with the course
- This entire R course website

It enables you to:

- save and execute code and display its output
- create high quality reports that could include [LaTeX](https://www.latex-project.org/) equations

What is great about [R Markdown](https://rmarkdown.rstudio.com/) documents is that they are fully reproducible and support many static and dynamic output formats, to name a few: PDF, HTML, MS Word, Beamer...  You can incorporate narrative text and code of your data analysis to produce an elegantly formatted story telling journey.

It is a variant of [Markdown](https://daringfireball.net/projects/markdown/) that has embedded **R code chunks** (denoted by three back ticks), to be used with [knitr](https://yihui.name/knitr/) to make it easy to create reproducible web-based reports. 

R Markdown is a plain text file that has the extension <span style="color:red">.Rmd</span>

To use **R Markdown** you will need to install the package from [CRAN](https://cran.r-project.org/) and load it with:


```r
install.packages("rmarkdown", repos = "http://cran.us.r-project.org")
suppressPackageStartupMessages(library(rmarkdown))
```

### RMarkdown Appreciation

Before we start learning about `RMarkdown` let us do an exercise of RMarkdown appreciation 😇

#### 👉 Go to the following GitHub repo to download the material: <https://github.com/TanjaKec/RMarkdown4RR>

Inside the data folder you will find the following `csv` files:

- athlete_events.csv
- noc_regions.csv
- exyu_olympic.csv

{{% notice info %}}
Split into groups of three and discuss how you would produce a Word document or a PowerPoint presentation to present your findings for the following problem:
{{% /notice %}}

Open the `exyu_olympic.csv` file in Excel and try to:

-	Find the number of medals per team? 
-	Find the number of medals per team for the last Rio games?
-	Visualise data about the number of female and male athletes from ex YU countries available in the data set.

We will work on this for the next 10 minutes. 🕟😬

We already have the R code that will provide the results for those questions. 👆😅

Open the `RMarkdown4RR.Rproj` file. Once you get RStudio up and running for the given project click on the "R/script1.R" file and run it chunk by chunk. 👏👏👏

The question we have now is: Can we put this into a document or a presentation? 🤔
Of course we can, but we need to learn how to do it. 🤓

### Starting with RMarkdown

**<span style="color:red">Task 1</span>:**
Open the file `RMarkdown_Intro.Rmd`

- Change the title of the Markdown Document from `My First Markdown Document` to `RMarkdown Introduction`.

-  Click the **"Knit"** button to see the compiled version of your sample code.


##### Congratulations! You’ve just Knitted your first Rmd document!!!! 👍😃

#### Basic Text editing

**<span style="color:red">Task 2</span>:**
Let’s format this document further by

- Changing the author of the document to your own name

- Rewriting the first sentence of the document to say "This is my first R Markdown document"

- Recompiling the document so you can see your changes

#### Adding a link

You can turn a word into a link by surrounding it in **hard brackets: [ ]** and then placing the link behind it in **parentheses: ( )**, like this:

`[RStudio](www.rstudio.com)`

**<span style="color:red">Task 3</span>:**
Make GitHub in the following paragraph link to https://github.com/TanjaKec/RMarkdown4RR

#### Text formatting 

To embed formatting instructions into your document using Markdown, you
would surround text by:

- one asterisk to make it italic: *italic*

- two asterisks to make it bold: **bold** and

- backticks to make it monospaced: `monospaced`.

To make an ordered list you need to place each item on a new line after a
number followed by a period followed by a space:
1. order list
2. second item

{{% notice note %}}
💡! Note that you need to place a blank line between the list and any paragraphs
that come before it.
{{% /notice %}}


<span style="color:red">**Task 4**</span>:

- Make the following paragraph in your Rmd document look like this:

When analysing data... The variables can be one of two broad types:

1) **Attribute variable**: has its outcomes described in terms of its characteristics or
attributes;

2) **Measured variable**: has the resulting outcome expressed in numerical terms.

- Make the word Knit in the following paragraph italic.


#### Embedding the `R` code 
To embed an R code chunk you would use three back ticks:

<p><code  class="r"> ```{r} </code>

` chunk of code`

<p><code  class="r"> ``` </code>

**<span style="color:red">Task 5</span>**: Replace the `cars` data set with the `gapminder` data set. Don't forget to load the `gapminder` package using `library(gapminder)`.

{{% notice warning %}}
If you haven't got the `gapminder` package available in your system you will need to install it: 
`install.packages("gapminder")`.
{{% /notice %}}


#### Prevent printing of the `R` code

You can also embed plots by setting `echo = FALSE` to the code chunk to
prevent printing of the R code that generates the plot:

<p><code  class="r"> ```{r, echo=FALSE} </code>

` chunk of code`

<p><code  class="r"> ``` </code>

**<span style="color:red">Task 6</span>**: Replace the base boxplot of `mpg` vs. `cyl` by a `ggplot`'s boxplot to examine a relationship between `continent` and `lifeExp` (note that you can use some of the `dplyr` functions!).



```r
suppressPackageStartupMessages(library(dplyr))
library(ggplot2)
# ggplot boxplot
ggplot(gapminder, aes(x = continent, y = lifeExp)) +
  geom_boxplot(outlier.colour = "hotpink") +
  geom_jitter(position = position_jitter(width = 0.1, height = 0), 
              alpha = .2) +
  labs (title= "Life Exp. vs. Continent", 
        x = "Continent", y = "Life Exp.") +
  theme(legend.position = "none", 
        panel.border = element_rect(fill = NA, 
                                    colour = "black",
                                    size = .75),
        plot.title=element_text(hjust=0.5))    
```

#### Adding **LaTex** equations

Finally, if you wish to add mathematical equations to your Markdown document you can easily embed [LaTeX]( LaTeX ) maths equations into your report.

To *display an equation* **in its own line** it needs to be surrounded by the double dollar symbol:

`$$` `y = a + bx` `$$`, 

or to *embed an equation* **in line within the text** you would use only one dollar symbol: `$y = a + bx$`.

**<span style="color:red">Task 7</span>**: Display the equation in the *Including Mathematical Equations* paragraph into its own line.


#### Congratulations! You have got the basics to start creating your own fabulous dynamic documents… !!!! 👍😃

### Taking a Step Further

Now you've got the basics of `rmarkdown` we will move on to editing more sophisticated features of your dynamic document.

When creating an HTML document from R Markdown, you need to specify the HTML document output format in the YAML metadata of your document. You can learn more about it by checking [this chapter](https://bookdown.org/yihui/rmarkdown/html-document.html) of [R Markdown: The Definitive Guide](https://bookdown.org/yihui/rmarkdown/) book.

Let us go through the next set of prepared `.rmd` files in your `RMarkdown4RR` project folder.

Do you remember our RMarkdown Appreciation exercise? 😃 

There is a list of files you should open and knit to see what features are incorporated into the documents and to learn how it is done. 

- **File `01_rmdApprec.Rmd`** incorporates the R code given in `R/script1.R` file. Open this `Rmd` file and check its metadata. Try to play around with the document's layout by changing some of the features, such as the table of contents (TOC) using the toc option or theme (for more available themes you can use see the blog post [r-markdown-theme-gallery](http://www.datadreaming.org/post/r-markdown-theme-gallery/). 

- **File `02_rmdApprec.Rmd`** enables you to create scientific and technical writing, native to the web by using the Distill Basics template. For more see <https://rstudio.github.io/distill/basics.html>.

- **File `03_rmdApprec.Rmd`** shows you how to add a static image file to your document. You should check the following blog post [Tips and tricks for working with images and figures in R Markdown documents](http://zevross.com/blog/2017/06/19/tips-and-tricks-for-working-with-images-and-figures-in-r-markdown-documents/) by [Zev Ross](http://www.zevross.com).

- **File `04_rmdApprec.Rmd`** illustrates happy collaboration with Rmd to docx. 

- **File `05_rmdApprec.Rmd`** shows how to put your work into a slide show.

- **File `06_rmdApprec.Rmd`** is a slide show you can upload on Rstudio's [RPubs](https://rpubs.com) server for sharing documents on the web.  

Install the [`rticles`](https://github.com/rstudio/rticles) package to get all of the available `rmd` templates for various paper articles.

{{% notice info %}}
This section is based on the material developed by [Dr Alison Hill](https://alison.rbind.io) for [R Markdown for Medicine](https://rmd4medicine.netlify.app) workshop.
{{% /notice %}}

R is a powerful tool for reproducible research. There are many other packages that you could also use for sharing your work. Creating Shiny application using the [R::Shiny](https://shiny.rstudio.com)  package is a nice way of engaging with the audience while sharing your work. Here is an example of reproducible research of the problem used in the [Resampling in the Undergraduate Statistics Curriculum](https://tatjanakec.shinyapps.io/permutation_bootstrap/_w_dc1f9850/Bootstrap_WhatTeacherShouldKnow.pdf) paper:

<https://tatjanakec.shinyapps.io/permutation_bootstrap/>

{{% notice note %}}
Reproducible research should not be a burden for anybody who takes their research seriously. If nothing else, the good habits of reproducibility may actually turn out to be a time-saver in the longer run for any research practitioner.
{{% /notice %}}


### Why use Git?

- Easy to use

- Making a mistake is not 'the end of the world'

- Allows you to keep a history of changes to your project through which it is easy to navigate

- Takes up minimal space


### Why use a Hosting Service Like Github

- Backup of your project

- No need for a server: easy to set up

- GitHub's strong community: your colleagues are probably already there

- Provides tools to help enhance collaboration

- A common location to share your work

##### Putting your R project on GitHub from RStudio

We will go through the basic steps of connecting RStudio with your GitHub account, but for more detailed instructions you should check [Happy Git with R](http://happygitwithr.com).

<img 
src="http://happygitwithr.com/img/watch-me-diff-watch-me-rebase-smaller.png" align="middle" img width="60%"  
/>

We are going to assume you are already familiar with and have done:

☑️ Chapter 5: [Register a GitHub account ](http://happygitwithr.com/github-acct.html)

☑️ Chapter 6: [Install or upgrade R and RStudio ](http://happygitwithr.com/install-r-rstudio.html)

* Go to your GitHub account and create a new repository

<img src="images/New_Repo.png" width="200px" style="display: block; margin: auto auto auto 0;" />

* Give it a meaningful name 
<img src="images/Create_New_Repo.png" width="300px" style="display: block; margin: auto auto auto 0;" />

* Copy repo's **HTTPS** address
<img src="images/HTTPS_GitHub.png" width="350px" style="display: block; margin: auto auto auto 0;" />

##### In RStudio

* Open a new project in RStudio: **File** ➡️ **New Project...**
<img src="images/RS_New_Project.png" width="250px" style="display: block; margin: auto auto auto 0;" />

* Select **Version Control** ➡️ **Git**
<img src="images/Select_Version_Control.png" width="250px" style="display: block; margin: auto auto auto 0;" />

* Paste the address of your Git repo  
<img src="images/set_up_git_connection.png" width="250px" style="display: block; margin: auto auto auto 0;" />
and check the box for `Open in new session` before you hit the `Create Project` button.

You're ready to go! 😃

**You would definitely find the following useful:**

- [RMarkdown cheatsheet](https://www.rstudio.com/wp-content/uploads/2016/03/rmarkdown-cheatsheet-2.0.pdf)

- [The R Markdown Reference Guide](https://www.rstudio.com/wp-content/uploads/2015/03/rmarkdown-reference.pdf)

- Book: [R Markdown: The Definitive Guide](https://bookdown.org/yihui/rmarkdown/)

- [Getting started with R Markdown](https://www.rstudio.com/resources/webinars/getting-started-with-r-markdown/)

- [R Markdown Quick Tour](https://rmarkdown.rstudio.com/authoring_quick_tour.html)

- [Advanced R Markdown – Tutorial::RStudio Conference 2017](https://www.rstudio.com/resources/videos/advanced-r-markdown-tutorial/)

- [Writing in R Markdown](https://jdblischak.github.io/r-intermediate-altmetrics/09-rmarkdown.html) by [Software Carpentry](https://software-carpentry.org/)

- [Tables Generator](https://www.tablesgenerator.com/markdown_tables)

-----------------------------
Material is released under a [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).

![](/images/cc_by_sa.jpg?width=5pc)
