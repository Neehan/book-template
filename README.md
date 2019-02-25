# book-template

This is the template I wrote for the book *কম্বিনেটরিকসে হাতেখড়ি* (Introduction to Combinatorics). This is the first Bengali book created with LaTeXbangla, a package I also wrote some years ago. I hope the style files will assist prospective authors to produce high quality Bangla books in future. 

## Build Instructions
**Fonts:** You'll need `SolaimanLipi`, `SiyamRupali` and `Monotype Corsiva` to build this project. They are not in the repo, as I do not have permission to distribute them. So, you have to install them separately. The output was somewhat different when the fonts were globally installed vs when the font files were placed in the root directory. I don't know the underlying cause. If your output does not match with `main.pdf`, try the other method. Note that, if you put the font files in the root directory, the file names have to be same as the names above. (For instance, the file for Kalpurush must be named `Kalpurush.ttf`)

**LaTeX:** You must have a LaTeX distribution installed in your system. If you are on Windows, you may install MikTeX. And, if you are on Linux, try TeXWorks. To compile, run `main.tex` with XeLaTeX and BibTeX. In Windows, the simplest way would be to open `main.tex` with MikTeX's default Editor, called TeXworks, then hit Build with `XeLaTeX+BibTeX+MakeIndex`. 

## How to Use
### File Description
`main.tex`: Essentially contains the structure of this project.

`bookbib.bib`: Bibliography.

`bookstyle.sty`: Contains the code for formatting.

`latexbangla.sty`: The package LaTeXbangla, but with more features. It is called by `bookstyle.sty`.

I have extensively commented in both `bookstyle.sty` and `latexbangla.sty`. They should be pretty easy to read. If not, please raise an issue.

### General Guidelines
Your book should be partitioned by chapters. Each chapter should be placed inside `chap` directory, in its own file. Then add the chapter to `main.tex` with `\include` command. Your figures should be placed inside `img` directory. They should also be partitioned by chapters. Lastly, your bibliography should be placed in `bookbib.bib`. 

**`\parskip` and `\[...\]`:** In LaTeX, two blocks of text separated by a blank line are considered as separate paragraphs. In this template, the extra spacing between paragraphs (unless required for layout) is `4pt`. This causes some unexpected behaviours. Consider this:

```
blah blah blah

\[a + b\]

more blah more blah
\[c+d\]
```

The output will look like this:

```
blah blah blah

a + b
more blah more blah
c+d
```

`\[a+b\]` is considered as a separate paragraph, as a result, there is some extra space between first line and a+b. It is quite noticable and rather assymetric. This is different from "vanilla" LaTeX where the output would have been

```
blah blah blah
a + b
more blah more blah
c+d
```
because of no extra spacing between paragraphs. Please keep it in mind that all the displaystyle environments, such as `equation`, `aligned*`, `split` etc. will also be affected. The solution is very simple: don't put an empty line between text and displaymath environment.

```
blah blah blah
\[a + b\]
more blah more blah
\[c+d\]
```


You may read the source of Pigeonhole Principle for guidance but do not blindly follow its style. See the section below.

## Things you should NOT follow
**What is `\phpname`?**
When I wrote Pigeonhole Principle, I was quite unsure whether I should translate or transliterate the title. I went with transliteration at that time. I put the title inside `\phpname`, because if I ever changed my mind, I would have to update the title only at one place. **You don't need to follow this style.** 


**Why are you manually controlling vertical spacing?**
This was the final fine-tuning step after all the rewriting, proofreading, and page settings had been gone through. The content was pretty much set to stone at that point. In general, **DO NOT USE `\vspace` arbitrarily,** especially, when you are haven't finished writing a chapter. You won't believe how much of it is going to change once you talk with your editor.

**Why are you placing multiple figures in a `tabular`?**
I am aware of the `\subbottom` command of `memoir` class. However, most of the time, I forget its name. Then I need to look it up in the documentation. So, I got lazy at one point and started using `tabular` instead. However, you should do it properly if you can.

**My figures are all over the place. Should I reposition them?**
If you aren't done writing a chapter, don't even bother. If you are sending the manuscript to your editor, then maybe care a little, but don't fret over it. Once you are sure the content, page layout, font size etc. are not going to change, only then reposition the figures. However, don't use `[H]` option from `float` package unless you know what you are doing. It breaks too many things down the line to be useful. Either use `placeins`, or resize your figures, whichever you prefer.

## License
This work may be distributed and/or modified under the conditions of the GPL v.3. If you do write a book with it, please give me credit and provide a link to this repo in the acknowledgements. This will also help prospective authors to find this template.
