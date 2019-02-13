---
title: 'Lepton: An automaton for Literate Executable Papers'
tags:
  - Ocaml
  - literate programming
  - reproducible research
authors:
  - name: Sébastien Li-Thiao-Té
    orcid: 0000-0002-4977-4969
    affiliation: "1" 
affiliations:
 - name: Université Paris 13, Sorbonne Paris Cité, LAGA, CNRS UMR 7539
   index: 1
date: 12 July 2018
bibliography: biblio_lepton.bib
---

# Summary

Source code is very hard to maintain when the documentation is missing. Recognizing
this fact, D. Knuth [@Knuth84literateprogramming] proposed the literate programming
paradigm, i.e. that source code and documentation should be written at the
same time, inside the same file, and in a format designed for human understanding.

''Lepton'' adds documents such as data analysis reports and scientific papers to this
vision. To enable reproducible research, ''Lepton'' makes it easy to include scripts
or complete programs, compilation and execution instructions, as well as execution
results in the same file. Offloading execution to ''Lepton'' makes the analysis
operator-independent and easy to reproduce. In the spirit of literate programming,
the plain text file format used by ''Lepton'' is intended to be human-understandable
as opposed to machine-readable, and simple enough to be usable without the software.

''Lepton'' consists in a standalone executable that processes plain text files
written in a documentation format such as HTML or LaTeX with optional blocks that
can contain files to be written to disk, source code or executable instructions.
It is distributed as a ''Lepton'' file containing the full source code, manual and a tutorial.
The package contains an extracted copy of the source code that can be compiled without ''Lepton''.

# Documentation
- `lepton_manual.pdf` contains usage instructions
- `lepton.pdf` contains the implementation details.

# Installation
The `lepton.bin` executable can be compiled with the included `make.sh` script. 

Requirements
- [OCaml](https://ocaml.org/docs/install.html) > 4.0

# Bootstrapping
The contents of the installation package can be re-generated from the file `lepton.nw`. This will produce a new executable, extract copies of the source files, and compile the LaTeX documentation.

Requirements
- [LaTeX](https://www.latex-project.org/)
- [Pygments](http://pygments.org) for syntax highlighting and the `minted` [LaTeX package](https://ctan.org/pkg/minted?lang=en)

Steps :
- process the main source file with Lepton `lepton lepton.nw -o lepton.tex`
- compile the main documentation file with LaTeX

```
xelatex -shell-escape -8bit lepton.tex
bibtex lepton.aux
xelatex -shell-escape -8bit lepton.tex
xelatex -shell-escape -8bit lepton.tex # LaTeX needs to execute twice to resolve references
```

# Contributing
If you wish to report bugs, please use the issue tracker at Github. If you would like to contribute to Lepton, just open an issue or a merge request.
