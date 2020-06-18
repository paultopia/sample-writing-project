---
title: "Sample Project Title"
author: Paul Gowder
bibliography: cites.json
date: June 18, 2020
---

# Hi!  I'm a sample project!

This is a sample project for [my academic writing workflow!](https://techup.lawyer/my-academic-writing-toolkitworkflow.html).  If you're coming to this repo from anywhere else, go back and read that post to see what I'm going on about.

If you look at the "raw" source of this document, you'll see what a basic markdown file looks like; in addition, the lines at the beginning of the document (surrounded in the source by triple-dashes) are *metadata*---information that is passed to pandoc to tell it what the final document should look like. 

Also in this library is a file called "cites.json."  This is a sample citation file, produced by Zotero with the help of Better Bibtex (it contains a bunch of stuff I wrote).  The fact that that file is here, and is referred to in the metadata to this file, means I can do something like cite myself [@gowder2018rtrom], and then when this file is built by Pandoc, it'll have a proper citation!  Incidentally, I don't have to use the default citation format; I can also include a different ["style file"](https://citationstyles.org) and refer to it appropriately in the metadata, to ask Pandoc to render mycitations in, for example, APA, MLA, Chicago, or even Bluebook (though the Bluebook version is kinda shaky, and if you really care about Bluebook working well, you should probably look into using [Juris-M](https://juris-m.github.io), which is a fork of Zotero designed specifically for legal stuff.  I don't really bother, because the Bluebook stuff I can get out of my setup is good enough, my standards for citation format correctness are low).

In order to convert this file to pdf, I then went to the commandline and typed in: 

```
pandoc -o sample.pdf -s --pdf-engine=xelatex --filter pandoc-citeproc readme.md
```

Breaking down that command: 

- Pandoc is the name of the application that does the magic 
- `-o` is a "flag" for Pandoc that means "the next thing on the commandline is going to be the name of the output file." Pandoc is smart enough to know that if it gets a ".pdf" extension it should produce a pdf file.
- `-s` means "produce a standalone file," it's a Pandoc quirk, don't worry about it, I just stick it in everywhere.
- `--pdf-engine=xelatex` is a little bit arcane, but, basically, it asks Pandoc to use a different application from the default one to compile PDFs---a much better one that lets you do things like easily switch fonts.
- `--filter pandoc-citeproc` asks Pandoc to invoke the "citeproc" "filter," which is a sub-application that goes in and swaps out all the citation keys for real citations before building the document. 
- And then readme.md is this file.

If you have Pandoc and LaTeX is installed, you should be able to clone this repository to your own computer (or download it as a zip file and then unzip it) and do the same thing.^[Incidentally, you might not be able to use git on a mac unless you've also either installed XCode, which is Apple's gigantic IDE (bloated developer application), or installed the lightweight version, also known as the XCode command line tools.  To do the latter, type `xcode-select --install` at a command line.]  Try it yourself!  Also, try switching the extension to ".docx" to get a Word file (take out the `pdf-engine` part).

**NOTE**: your PDF won't look exactly the same as mine.  That's because I've fairly extensively messed with some of the Pandoc defaults to get PDF files coming out looking exactly the way I like every time.  But your PDF will still come out pretty---and I'll bet you'll find that they come out prettier than the stuff Word produces.^[On the other hand, my customizations *require* that extra chunk of commandline noise for changing the PDF engine, because I've done a lot of manipulations to typefaces and the like.  You won't need that for yours, probably.]

## References