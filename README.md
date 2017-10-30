# docker-latex-genealogytree

Container for building genealogy trees in LaTeX (using TeXlive and the wonderful [genealogytree package](https://ctan.org/pkg/genealogytree)).


## Building The Image

    docker build -t jojomi/latex-genealogytree .


## Compiling a genealogy tree

Usually you would set your working directory and then call little scripts in `bin` directory:

    cd example
    ../bin/pdflatex

This will compile `document.tex`. You can add parameters and change the latex binary (support for `pdflatex`, `xelatex`, and `lualatex` is included):

    ../bin/lualatex document.tex

If you want those binaries to be globally available, you'll have to put them in your `PATH`. Check its current value like this:

    echo $PATH

Now pick one of the directories listed there and link the scripts there:

```
for f in bin/*; do sudo ln -s "$(pwd)/$f" /usr/local/bin/$(basename $f); done
```


For more technical details have a look at the [base image](https://github.com/jojomi/docker-latex) used.
