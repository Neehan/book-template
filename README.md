# book-template

This is the template for the first Bengali book written with LaTeXbangla, a package I have written some years ago. I hope the style files will simplify a number of steps in producing high quality Bengali books in LaTeX. 

## Build Instructions
**Fonts:** You'll need `SolaimanLipi`, `SiyamRupali` and `Monotype Corsiva` to build this project. They are not in the repo, so you have to install them separately. Note that there was noticable difference in output when the fonts were globally installed and when the font files were placed in the root directory. I don't know the underlying cause, however, if your output does not seem to match with `main.pdf`, try the later apporach. The font files should be named exactly as given.

**LaTeX:** You must have a LaTeX distribution installed in your system. If you are on Windows, you may install MikTeX. And, if you are on Linux, try TeXWorks. To compile, run `main.tex` with XeLaTeX and BibTeX. In Windows, the simplest way would be to open `main.tex` with MikTeX's default Editor, called TeXworks, then hit Build with `XeLaTeX+BibTeX+MakeIndex`. 

## How to Use
I have extensively commented in both `bookstyle.sty` and `latexbangla.sty`. Your source code should be partitioned by chapters. Each chapter should be placed inside `chap` directory, and associated images should be placed inside `img` directory. Your bibliography should be placed in `bookbib.bib`. You may read the source of Pigeonhole Principle for guidance but do not blindly follow its style. See the section below.

## Things you should NOT follow
**What is `\phpname`?**
When I wrote Pigeonhole Principle, I was quite unsure if should translate the title, or transliterate it. I went with transliteration, but put the title inside a command. This is because if I ever changed my mind, I would have to update the title only at one place. **You don't need to follow this style.** 


**Why are you manually controlling vertical spacing?**
This was the final fine-tuning step after all the rewritting, proofreading, and page settings had been gone through. The content was pretty much set to stone at that point. In general, **DO NOT USE `\vspace` arbitrarily,** especially, when you are writiing a book. You won't believe how much of it is gonna change once you talk with your editor.

**Why are you placing multiple figures in a `tabular`?**
I am aware of the `\subbottom` command of `memoir` class. However, most of the time, I forget its name and I need to look it up in the documentation. So, I got lazy at one point and started using `tabular` instead. However, you should do it properly if you can.

**My figures are all over the place. Should I reposition them?**
If you aren't done writing a chapter, don't even bother. If you are sending the manuscript to your editor, then maybe care a little, but don't spend too much time on it. Once you are sure the content, page layout, font size etc. are not gonna change, only then reposition the figures. However, don't use `[H]` from float unless you know what you are doing. It breaks too many things down the line to be useful. Either use `placeins`, or resize your figures, whichever you prefer.

## License
This work may be distributed and/or modified under the conditions of the GPL v.3. If you do write a book with it, please give me credit and provide a link to this repo in the acknowledgements. This will also help future authors to find this template.