
# PsyTeachR Style Guide

The following are specific recommendations to make our course materials look and act consistently to help students navigate more easily from one year to the next. These styles will be continuously evolving, so do discuss with the team if any recommendations don't meet your needs or you want to propose new recommendations.

## General styles

### Headers

Level 1 headers (i.e., chapter titles) should be title case. The first letter of all words should be uppercase except articles, prepositions, and be verbs in the middle of the title (e.g., a, an, the, is, are in, on).

Level 2 or higher headings should start with an uppercase letter (unless they are the name of a function or package that starts with a lowercase letter: e.g., **`tidyverse`**) and the rest of the heading should be lowercase (except proper nouns: e.g., RStudio, R, psyTeachR, Niamh).

You can link to a header using the syntax `[link text](#Header-title-with-dashes)`. If the header title is long, you can make a shorter reference by adding `{#shortname}` after the header and reference it like `[link text](#shortname)`. You can reference the section by section number this way: `\@ref(shortname)` and the number will automatically link to the section (e.g., Section \@ref(torf)).

Chapters should **usually** have between three and eight level 2 headers. There will obviously be exceptions, but if you consistently have more or fewer sections, think about restructuring your content. See the section on [special headers](https://bookdown.org/yihui/bookdown/markdown-extensions-by-bookdown.html#special-headers) in the Bookdown book to learn how to divide your book into parts.


### Text styles

* Emphasised text should be **bold** (e.g., `**bold**`)
* Avoid italics and underlining for dyslexia-friendly reading
* Exactly quoted names of buttons or interface objects should be **`bold code`** (e.g., ``` **`bold code`** ```)
* Inline code should be in `backticks` (e.g., ``` `backticks` ```)
    * Package names should be in backticks (e.g., ``` `tidyverse` ```)
    * Function names should be in backticks with brackets (e.g., ``` `rnorm()` ```)

### Links

Links to pages in the psyteachr site should be normal internal links (e.g., `[link text](url)`. If you are linking to an external resource, use the following style: `[link text](url){target="_blank"}` to create a link that looks and behaves like this: [RStudio](https://rstudio.com/){target="_blank"}.

### Lists

Lists where most of the items fit on one line should start each line with an uppercase letter (unless the first word is code where case is important) and there should be no blank lines between items. 

```
* Item 1
* Item 2
* Item 3
```

* Item 1
* Item 2
* Item 3


### Tables

Use `knitr::kable()` to output tibbles as a table. Set `results='asis'` in the code chunk header. Set the caption in the `caption` argument to `kable` and use `\@ref(tab:chunk-name)` to reference the table (e.g., Table \@ref(tab:kable-example)).


```r
iris %>%
  group_by(Species) %>%
  summarise_all(mean) %>%
  knitr::kable(digits = 3, caption = "Example table with kable.")
```



Table: (\#tab:kable-example)Example table with kable.

Species       Sepal.Length   Sepal.Width   Petal.Length   Petal.Width
-----------  -------------  ------------  -------------  ------------
setosa               5.006         3.428          1.462         0.246
versicolor           5.936         2.770          4.260         1.326
virginica            6.588         2.974          5.552         2.026

If you want to add stripes or fancy styling to your tables, install the package `kableExtra` [@R-kableExtra]. This [vignette](https://cran.r-project.org/web/packages/kableExtra/vignettes/awesome_table_in_html.html) has great examples of other things you can do with table display.


```r
iris %>%
  group_by(Species) %>%
  summarise_all(mean) %>%
  knitr::kable(digits = 3, format = "html", caption = "Example table with kableExtra.") %>%
  kableExtra::kable_styling(bootstrap_options = "striped")
```

<table class="table table-striped" style="margin-left: auto; margin-right: auto;">
<caption>(\#tab:kable-example-striped)Example table with kableExtra.</caption>
 <thead>
  <tr>
   <th style="text-align:left;"> Species </th>
   <th style="text-align:right;"> Sepal.Length </th>
   <th style="text-align:right;"> Sepal.Width </th>
   <th style="text-align:right;"> Petal.Length </th>
   <th style="text-align:right;"> Petal.Width </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> setosa </td>
   <td style="text-align:right;"> 5.006 </td>
   <td style="text-align:right;"> 3.428 </td>
   <td style="text-align:right;"> 1.462 </td>
   <td style="text-align:right;"> 0.246 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> versicolor </td>
   <td style="text-align:right;"> 5.936 </td>
   <td style="text-align:right;"> 2.770 </td>
   <td style="text-align:right;"> 4.260 </td>
   <td style="text-align:right;"> 1.326 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> virginica </td>
   <td style="text-align:right;"> 6.588 </td>
   <td style="text-align:right;"> 2.974 </td>
   <td style="text-align:right;"> 5.552 </td>
   <td style="text-align:right;"> 2.026 </td>
  </tr>
</tbody>
</table>

## Glossary

You can use the glossary function to automatically link to a term in the [psyTeachR glossary](https://psyteachr.github.io/glossary/) and automatically include a tooltip with a short definition when you hover over the term. Use the following syntax in inline r: `glossary("word")`. For example, common <a class='glossary' target='_blank' title='The kind of data represented by an object.' href='https://psyteachr.github.io/glossary/d#data-type'>data types</a> are <a class='glossary' target='_blank' title='A data type representing whole numbers.' href='https://psyteachr.github.io/glossary/i#integer'>integer</a>, <a class='glossary' target='_blank' title='A data type representing a real decimal number' href='https://psyteachr.github.io/glossary/d#double'>double</a>, and <a class='glossary' target='_blank' title='A data type representing strings of text.' href='https://psyteachr.github.io/glossary/c#character'>character</a>.

If you need to link to a definition, but are using a different form of the word, add the display version as the second argument (`display`). You can also override the automatic short definition by providing your own in the third argument (`shortdef`). Add the argument `link = FALSE` if you just want the hover definition and not a link to the psyTeachR glossary.


```r
glossary("data type", 
         display="Data Types", 
         shortdef="My custom definition of data types", 
         link = FALSE)
```

[1] "<a class='glossary' title='My custom definition of data types'>Data Types</a>"

You can add a glossary table to the end of a chapter with the following code. It creates a table of all terms used in that chapter previous to the `glossary_table()` function.

<div class='verbatim'><code>&#96;&#96;&#96;{r, echo=FALSE, results='asis'}</code>

```r
glossary_table()
```

<code>&#96;&#96;&#96;</code></div>

<table>
 <thead>
  <tr>
   <th style="text-align:left;"> term </th>
   <th style="text-align:left;"> definition </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> <a class='glossary' target='_blank' href='https://psyteachr.github.io/glossary/c#character'>character</a> </td>
   <td style="text-align:left;"> A data type representing strings of text. </td>
  </tr>
  <tr>
   <td style="text-align:left;"> <a class='glossary' target='_blank' href='https://psyteachr.github.io/glossary/d#data-type'>data-type</a> </td>
   <td style="text-align:left;"> My custom definition of data types </td>
  </tr>
  <tr>
   <td style="text-align:left;"> <a class='glossary' target='_blank' href='https://psyteachr.github.io/glossary/d#double'>double</a> </td>
   <td style="text-align:left;"> A data type representing a real decimal number </td>
  </tr>
  <tr>
   <td style="text-align:left;"> <a class='glossary' target='_blank' href='https://psyteachr.github.io/glossary/i#integer'>integer</a> </td>
   <td style="text-align:left;"> A data type representing whole numbers. </td>
  </tr>
</tbody>
</table>



If you want to contribute to the glossary, fork the [github project](https://github.com/PsyTeachR/glossary), add your terms and submit a pull request, or suggest a new term at the [issues page](https://github.com/PsyTeachR/glossary/issues).

## Word choice

In general, use UK spelling and terminology. Use the `colour` version of functions in `ggplot2`.

There is a lot of cultural variation in what we call punctuation and symbols. For psyTeachR books, use the conventions in Appendix \@ref(symbols).

Use the following conventions for proper nouns:

* RStudio
* R Markdown (this is how Yihui Xie writes it)
* LaTeX (you don't have to be fancy with ${\LaTeX}$)



## Colour

Logo colours are from the University of Glasgow palette.

* <span style="color: var(--pink);">pink: #983E82</span>
* <span style="color: var(--orange);">orange: #E2A458</span>
* <span style="color: var(--yellow);">yellow: #F5DC70</span>
* <span style="color: var(--green);">green: #59935B</span>
* <span style="color: var(--blue);">blue: #467AAC</span>
* <span style="color: var(--purple);">purple: #61589C</span>

If you are comfortable editing css and want to add styles with colour, you can add the theme colours to css with the keywords using this pattern:

```
* <span style="color: var(--purple);">Some purple text</span>
* <span style="background-color: var(--yellow);">Yellow background</span>
```

<div class="info">
<p>Remember to test your materials with the <strong>Sepia</strong> and <strong>Night</strong> themes. Add additional styles for sepia (<code>div.color-theme-1</code>) and dark (<code>div.color-theme-2</code>) backgrounds.</p>
</div>

You can also access the psyTeachR colours in R from the function `psyteachr_colours()` (or `psyteachr_colors()`).


```r
psyteachr_colours()    # gives all 6 colours
psyteachr_colours(1:3) # specify colours by number
c("pink", "yellow", "blue") %>% # specify by name
  psyteachr_colours()           # Lisa loves pipes
```

```
## [1] "#983E82" "#E2A458" "#F5DC70" "#59935B" "#467AAC" "#61589C"
## [1] "#983E82" "#E2A458" "#F5DC70"
## [1] "#983E82" "#F5DC70" "#467AAC"
```


```r
tibble(
  grp = rep(LETTERS[1:6], each = 20),
  val = rep(1:6, each = 20) + rnorm(20*6)
) %>%
  ggplot(aes(grp, val, fill = grp)) +
  geom_violin() +
  scale_fill_manual(values = psyteachr_colours())
```

<div class="figure" style="text-align: center">
<img src="02-style-guide_files/figure-html/plot-psyteachr-colours-1.png" alt="Plot with psyteachr.colours" width="50%" />
<p class="caption">(\#fig:plot-psyteachr-colours)Plot with psyteachr.colours</p>
</div>


## Figures

Use `\@ref(fig:chunk-name)` to link to and reference the figure number in text (e.g., Figure \@ref(fig:img-dynamo)). You can learn more about including figures and images in the [Bookdown book](https://bookdown.org/yihui/bookdown/figures.html).

<div class="danger">
<p>The chunk label for figures can only contain alphanumeric characters (a-z, A-Z, 0-9), slashes (/), or dashes (-). Otherwise, they are not automatically numbered.</p>
</div>

### R Plots

Any graphs should be dynamically created in an R code block. Set `echo=FALSE` if you don't want to display the code that creates a plot. Default values are specified below; you don't have to include those unless you want to change them, but always set the `fig.cap`.

* `out.width='100%'`
* `fig.align='center'`
* `fig.width=8`
* `fig.height=5`
* `fig.cap='**CAPTION THIS FIGURE!!**'`

<div class='verbatim'><code>&#96;&#96;&#96;{echo=FALSE, out.width='75%', fig.width=6, fig.height=2.5, fig.cap='Dynamically created plot.'}</code>

```r
ggplot(iris, aes(Sepal.Length, Sepal.Width, color = Species)) +
  geom_point() +
  geom_smooth(method = lm)
```

<code>&#96;&#96;&#96;</code></div>

<div class="figure" style="text-align: center">
<img src="02-style-guide_files/figure-html/img-dynamo-1.png" alt="Dynamically created plot." width="75%" />
<p class="caption">(\#fig:img-dynamo)Dynamically created plot.</p>
</div>


### Images

Static images, like screenshots, should be stored in a directory called **images** and displayed using the `knitr::include_graphics` function in a code block.

<div class='verbatim'><code>&#96;&#96;&#96;{r img-psyteacher-logo, echo=FALSE, fig.cap="PsyTeachR Logo"}</code>

```r
knitr::include_graphics("images/psyteachr_logo.png")
```

<code>&#96;&#96;&#96;</code></div>

<div class="figure" style="text-align: center">
<img src="images/psyteachr_logo.png" alt="PsyTeachR Logo displayed by the previous code block." width="100%" />
<p class="caption">(\#fig:img-psyteacher-logo)PsyTeachR Logo displayed by the previous code block.</p>
</div>


### Screenshots

You'll probably want to include some screenshots of RStudio. For consistency, make sure your Rstudio is set to the default editor theme (Modern editor with Text-Mate theme and Consolas font). Set the font size to at least 18 for readability in screenshots.

<div class="figure" style="text-align: center">
<img src="files/images/default_editor.png" alt="Default RStudio editor settings." width="50%" />
<p class="caption">(\#fig:img-default-editor)Default RStudio editor settings.</p>
</div>

Keep panes in the default order.

* Upper left: Source
* Upper right: Environment, History, Connections, Build, Git
* Lower right: Files, Plots, Packages, Help, Viewer
* Lower left: Console
    
<div class="figure" style="text-align: center">
<img src="files/images/default_panes.png" alt="Default RStudio pane layout." width="100%" />
<p class="caption">(\#fig:img-default-panes)Default RStudio pane layout.</p>
</div>


## Code chunks

**Always name your code chunks**; this makes debugging easier and becomes the name of generated plots. You can duplicate chunk names between .Rmd files, but not within.

<div class="danger">
<p>The chunk label for tables and figures can only contain alphanumeric characters (a-z, A-Z, 0-9), slashes (/), or dashes (-). Otherwise, they are not automatically numbered. So just get into the habit of avoiding underscores.</p>
</div>

### Options

Code chunks can take several options The most common ones are explained below. [Learn more about code chunks](https://bookdown.org/yihui/rmarkdown/r-code.html).

* `eval`: set to `FALSE` to skip running the code
* `echo`: set to `FALSE` to skip displaying the code
* `include`: set to `FALSE` to run but show no output (e.g., code, figures, messages, warnings)
* `cache`: set to `TRUE` if you have a code chunk that takes a long time to run. It should run if you make changes, but doesn't always. Delete your cache and render the book from scratch before you push major updates
* `results`
    + "hold" to hold all the output pieces and display them after the code chunk (default for psyTeachR books)
    + "markup" to intersperse code and output as they happen
    + "hide" to hide output
    + "asis" to write raw results (like the output of `knitr::kable`)

### Including headers

If you want to show students an example of a code chunk that includes the header, add an option called `verbatim` to your code chunk and set it equal to what you want displayed inside the curly brackets. Make sure you set `eval=FALSE` to stop the code chunk from being run.

<div class='verbatim'><code>&#96;&#96;&#96;{r verbatim-example, eval = FALSE, verbatim = 'r chunk-name, messages=FALSE'}</code>

```r
library(tidyverse)
```

<code>&#96;&#96;&#96;</code></div>

<div class="info">
<p>The “verbatim” option is not standard to bookdown. It is only available if you include the code from the “R/psyteachr_setup.R” file.</p>
</div>


### Verbatim inline backticks

Include verbatim inline r like this <code>&#096;r backtick("r 3+4")&#096;</code> to produce output like this: <code>&#096;r 3+4&#096;</code>.


## Call-out Blocks {#call-out-blocks}

The psyTeachR course book style includes four types of *call-out blocks* that you can use to emphasise text.

### Danger

<div class='verbatim'><code>&#96;&#96;&#96;{block, type="danger"}</code>Note dangerous things that will break code.<code>&#96;&#96;&#96;</code></div>

<div class="danger">
<p>Note dangerous things that will break code.</p>
</div>

### Warning

<div class='verbatim'><code>&#96;&#96;&#96;{block, type="warning"}</code>Warn readers.<code>&#96;&#96;&#96;</code></div>

<div class="warning">
<p>Warn readers.</p>
</div>

### Info

<div class='verbatim'><code>&#96;&#96;&#96;{block, type="info"}</code>Give further information.<code>&#96;&#96;&#96;</code></div>

<div class="info">
<p>Give further information.</p>
</div>

### Try

<div class='verbatim'><code>&#96;&#96;&#96;{block, type="try"}</code>Stop and try something.<code>&#96;&#96;&#96;</code></div>

<div class="try">
<p>Stop and try something.</p>
</div>

### Code chunks inside call-out blocks

If you want to put code blocks inside of a call-out block, you can't use the syntax above. Start the block with `&lt;div class="danger">` and end it with `&lt;/div>`.

<pre><code>&lt;div class="danger">
Run the code below:

```r
# my code
```
&lt;/div></code></pre>

## References

Include references using the bibliography key, such as `@R-base`, which provides an in-line citation like @R-base. You can also use square brackets to create a parenthetical citation, like `[@R-bookdown]` [@R-bookdown]. 

You need to add any R packages you want to cite by adding them to the code chunk in the index file and then referencing them by `@R-pckgname`.


```r
# automatically create a bib database for R packages
# add any packages you want to cite here
knitr::write_bib(c(
  .packages(), 'bookdown', 'tidyverse'
), 'packages.bib')
```

Add other references to the `book.bib` file using BibTeX format. You can export references from most reference managers in BibTeX format.

[Learn more about referencing](https://bookdown.org/yihui/bookdown/citations.html).

