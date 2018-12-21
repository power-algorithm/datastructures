# A User's Guide to this Book

## Running Code

The code chunks throughout the book are executed in one of several ways.
The most basic way that these chunks are executed is using the *Mume* markdown processor.
The syntax used to pass parameters for code chunks is specific to Mume.
As it processes the markdown into html, it identifies the code chunks, executes them, and puts the output directly into the output.

The examples in the book can be executed directly inline with the right editor and plugins.
You will need to use the **Markdown Preview Enhanced** plugin for either Atom or Visual Studio Code.
This wonderful plugin allows for realtime preview and instant code execution right in the browser.

I recommend changing the settings to not break on single newlines.
I *try* to stick to the one-sentence-per-line policy to ease the process of reviewing git diffs.

### PYTHONPATH Issues

One challenge to running the code from two different locations involves python's system path.
For most code chunks, it's no problem.
However, for more complex data structures that need to import other modules from other chapters, Python will need to know where to look for the code.
The simplest fix is to simply add the `code/` directory to your python path.
I did this with the following line in my `.bash_profile` file.

```
export PYTHONPATH="/Users/don/Dropbox/work/research/books/datastructures/code:$PYTHONPATH"
```

This also solves the issue of running tests from the `tests/` folder.

## Making Improvements

All of the source for this book is available on github.
As a result, you can contribute improvements of your own.
A project of this scale always has bugs.
If you find a bug, you can fork the repository, fix the bug, and make a pull request.

There are a couple things to keep mind:

- Any code generated in the `code/` directory is scraped from the text in the prose folder.  
Edit the markdown file, not the `.py` file.
- Please add tests to the
- Similarly, the `fullbook*` files in the `docs/` directory are generated by the build.  
These files should also not be edited.
- Please avoid hard-wrapping lines.  I guess some people still do this.

## Building the book

Currently, the books build process has two steps.

1. Running the `generatebook.py` script will integrate all the chapters into a single markdown file.  It does a little extra to add chapter numbers and forced page breaks for print layouts.

2. Running `generatebook.js` from node will use mume to process the `fullbook.md` file into html and pdf.  The pdf export requires installing the Chrome Puppeteer node module (and Mume too of course).  This second step is in javascript because Mume is built on node.

To pull the code out of the book into separate `.py` files, you will need to run the `generatecode.py` script.

## Drawing figures

Currently, the book is light on figures.
I am working to integrate a system where data structures are drawn inline using svgs that get integrated directly into the resulting html.