# Introduction

[Troff](https://www.troff.org/) is a [system of programs](https://www.troff.org/prog.html) that process a textual description of a document to produce typeset versions suitable for printing. It's more `What you describe is what you get' rather than WYSIWYG.

[mdBook](https://rust-lang.github.io/mdBook/index.html) is a command line tool and Rust crate to create books using Markdown files. 

[Markdown](https://commonmark.org/) is a plain text format for writing structured documents, based on formatting conventions from email and usenet.
Here is the latest CommonMark specification of Markdown is [Version 0.29 (2019-04-06)](https://spec.commonmark.org/0.29).

## Troff in docker

The `Dockerfile` for troff (with modern [groff](https://www.gnu.org/software/groff/) implementation) is
```
FROM debian:stable
RUN apt-get update -qy
RUN apt-get install -qy make groff
RUN sed -i 's/papersize a4/papersize letter/' /usr/share/groff/current/font/devpdf/DESC # set groff papersize to letter
RUN dpkg -l
```
which generates an docker image of 374MB.
```
$ docker images
REPOSITORY                 TAG       IMAGE ID       CREATED          SIZE
2021-04-12-mdbook_troff    latest    e207ce03cafb   13 seconds ago   374MB
```

## mdBook in docker

The `Dockerfile` for mdBook has only two lines

```
FROM rust:latest
RUN cargo install mdbook
```
which generates a docker image of 1.45GB, 5 times larger than the troff.
```
$ docker images   
REPOSITORY                 TAG       IMAGE ID       CREATED             SIZE
2021-04-12-mdbook_mdbook   latest    d30a7ca05fc7   About an hour ago   1.45GB
```



