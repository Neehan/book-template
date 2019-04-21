# book-template

This is the template for the book (*কম্বিনেটরিকসে হাতেখড়ি* (Introduction to Combinatorics))[https://rokomari.com/book/180324/combinatoricse-hatekhori--1st-part]. It is the first Bengali book created with LaTeXbangla, a package I also wrote some years ago. I hope the style files will assist prospective authors to produce high quality Bangla books in future. 

## Build Instructions
**Fonts:** You'll need `SolaimanLipi`, `SiyamRupali` and `Monotype Corsiva` to build this project. They are not in the repo, as I do not have permission to redistribute them. So, download them from the internet and place the font files in the root directory. The file names have to be same as the names given above. (For instance, the file for Siyam Rupali must be named `SiyamRupali.ttf`)

**LaTeX:** You must have a LaTeX distribution installed in your system. I recommend MikTeX for Windows and TeXWorks for Linux. To build the project, run **XeLaTeX and BibTeX** on `main.tex`. In Windows, the simplest way would be to open `main.tex` with MikTeX's default Editor, called TeXworks, then hit Build with `XeLaTeX+BibTeX+MakeIndex`. 

## How to Use
### File Description
`main.tex`: Essentially contains the structure of this project.

`bookbib.bib`: Bibliography.

`bookstyle.sty`: Contains the code for formatting.

`latexbangla.sty`: The package LaTeXbangla, but with more features. It is called by `bookstyle.sty`.

I have extensively commented in both `bookstyle.sty` and `latexbangla.sty`. They should be pretty easy to read. If not, please raise an issue.

### General Guidelines
Partition your source code by chapters. Place every chapter inside `chap` directory, in its own file. Then add the chapters to `main.tex` with `\include` command. Your figures should be placed inside `img` directory. They should also be partitioned by chapters. Lastly, your bibliography should be in `bookbib.bib`. 

**`\parskip` and `\[...\]`:** Two blocks of text separated by a blank line are considered separate paragraphs in LaTeX. In this template, the extra spacing between paragraphs (unless required for layout) is `4pt`. It modifies LaTeX's default behaviours. Consider the following example:

```
blah blah blah

\[a + b\]
more blah more blah
\[c+d\]
```

The output will look like:

```
blah blah blah

a + b
more blah more blah
c+d
```

becase `\[a+b\]` is considered a separate paragraph. Consequently, there is some extra space between first line and a+b. It is quite noticable and rather assymetric. This is different from "vanilla" LaTeX where the output would have been

```
blah blah blah
a + b
more blah more blah
c+d
```
because of no extra spacing between paragraphs. Please keep it in mind that all the displaystyle environments, such as `equation`, `align`, `split` etc. will be affected. The solution is very simple: don't put an empty line between text and displaystyle environment.

```
blah blah blah
\[a + b\]
more blah more blah
\[c+d\]
```


You may read the source of Pigeonhole Principle for guidance but do not blindly follow its style. See the section below.

## Things you should NOT follow
**What is `\phpname`?**
When I wrote Pigeonhole Principle, I was quite unsure if I should translate or transliterate the title. I went with transliteration at that time. I put the title inside `\phpname`, because if I ever changed my mind, I would have to update the title only at one place. **You don't need to follow this style.** 


**Why are you manually controlling vertical spacing?**
This was the final fine-tuning step after all the rewriting, proofreading, and page settings had been gone through. The content was pretty much set to stone at that point. In general, **DO NOT USE `\vspace` arbitrarily,** especially, when you are haven't finished writing a chapter. Book editors will disagree with at least 25% of your first draft, so the final document will be noticibly different.

**Why are you placing multiple figures in a `tabular`?**
I am aware of the `\subbottom` command of `memoir` class, but forget its name when I need it. Then I need to look it up in the documentation. So, I got lazy at one point and started using `tabular` instead. However, you should follow the recommended method if you can.

**My figures are all over the place. Should I reposition them?**
If you aren't done writing a chapter, don't even bother. If you are sending the manuscript to your editor, then maybe care a little, but don't fret over it. Once you are sure the content, page layout, font size etc. are not going to change, only then reposition the figures. However, don't use `[H]` option from `float` package unless you know what you are doing. It breaks too many things down the line to be useful. Either use `placeins`, or resize your figures, whichever you prefer.

## License
This work may be distributed and/or modified under the conditions of the GPL v.3. If you do write a book with it, please give me credit and provide a link to this repo in the acknowledgements. This will also help prospective authors to find this template.
