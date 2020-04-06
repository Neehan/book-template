# book-template

Here you can find the template files for the book *কম্বিনেটরিকসে হাতেখড়ি* (Introduction to Combinatorics)[part 1](https://rokomari.com/book/180324/combinatoricse-hatekhori--1st-part), [part 2](https://www.rokomari.com/book/185613/combinatoricse-hatekhori--2nd-part). It is the first Bengali book written with LaTeXbangla, a package I authored some years ago. I hope this repo will assist prospective authors to produce high quality Bangla books in future. 

## Build Instructions
**Fonts:** You'll need `SolaimanLipi`, `SiyamRupali` and `Monotype Corsiva` to build this project. They are not in the repo, as I do not have permission to redistribute them. So, download them from the internet and place the ttf files in the root directory. The file names have to be same as the names given above. (For instance, the file for Siyam Rupali must be named `SiyamRupali.ttf`)

**LaTeX:** You must have a LaTeX distribution installed in your system. I recommend MikTeX for Windows and TeXWorks for Linux. To build the project, run **XeLaTeX and BibTeX** on `main.tex`. In Windows, the simplest way would be to open `main.tex` with MikTeX's default Editor, called TeXworks, then hit Build with `XeLaTeX+BibTeX+MakeIndex`. 

## How to Use
### File Description
`main.tex`: The big picture.

`bookbib.bib`: Bibliography.

`bookstyle.sty`: Code for formatting.

`latexbangla.sty`: The package LaTeXbangla with more features. It is called by `bookstyle.sty`.

I have extensively commented in both `bookstyle.sty` and `latexbangla.sty`. The code should be pretty easy to follow. If not, please raise an issue.

### General Guidelines
Partition your source code by chapters. Place every chapter inside `chap` directory, in its own file. Then add the chapters to `main.tex` with `\include` command. Your figures should be placed inside `img` directory and partitioned by chapters. Lastly, add your bibliography to `bookbib.bib`. 

**`\parskip` and `\[...\]`:** If two consecutive blocks of text are separeted by one or more blank lines, they are considered separate paragraphs in LaTeX. In this template, the spacing between consecutive paragraphs is set to be `4pt`. This might result in some 'surprises' as demostrated by the following example:
```
blah blah blah

\[a + b\]
more blah more blah
\[c + d\]
```
The output will look like:
```
blah blah blah

a + b
more blah more blah
c + d
```
becase `blah blah blah` and `\[a+b\]` are rendered as separate paragraphs. This is different from "vanilla" LaTeX where the output would have been

```
blah blah blah
a + b
more blah more blah
c + d
```
because of no spacing between paragraphs. The same behavior would be observed in all displaystyle environments, such as `equation`, `align`, `split` etc. The solution is very simple: don't put empty lines between text blocks and displaystyle environments.

```
blah blah blah
\[a + b\]
more blah more blah
\[c + d\]
```


You may read the source of Pigeonhole Principle for guidance but do not blindly follow its style. See the section below.

## FAQ
**What is `\phpname`?**
When I wrote Pigeonhole Principle, I was unsure if the title should be translated or transliterated. I went with transliteration at that time. I put the title inside `\phpname`, because if I ever changed my mind, I would have to update the title only at one place. **You don't need to follow this style.** 

**Why are you manually controlling vertical spacing?**
This was the final fine-tuning step after all the rewriting, proofreading, and page settings had been gone through. The content was set to stone at that point. In general, **DO NOT USE `\vspace` arbitrarily,** especially, when you are haven't finished writing a chapter. Book editors will disagree with at least one third of your first draft. Your publisher might want to change many other things, such as, font size, font type, margins etc. So, it makes no sense to spend time on style until the draft is final.

**Why are you placing multiple figures in a `tabular`?**
I am aware of the `\subbottom` command of `memoir` class, but hardly remember its name when I need it. So, I got lazy at one point and started using `tabular` instead. However, you should follow the recommended method if you can.

**My figures are all over the place. Should I reposition them?**
If you aren't done writing a chapter, don't even bother. If you are sending the manuscript to your editor, then maybe care a little, but don't fret over it. Once you are sure the content, page layout, font size etc. are not going to change, only then reposition the figures. However, don't use `[H]` option from `float` package unless you know what you are doing. It breaks too many things down the line to be useful. Either use `placeins`, or resize your figures, whichever you prefer.

## License
This work may be distributed and/or modified under the conditions of the GPL v.3. If you do write your book with it, please consider giving me credit and providing a link to this repo in the acknowledgements. This will also help the prospective authors to find this template.
