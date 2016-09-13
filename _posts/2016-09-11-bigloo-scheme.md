---
layout: post
title: Bigloo Scheme
category: Compilers
tags: ['Scheme', 'Bigloo']
published: true
---

## Bigloo

As part of my reading *Lisp in Small Pieces*, [Bigloo](http://www-sop.inria.fr/mimosa/fp/Bigloo/) is one of the Scheme compilers that I use as part of my development environment. I've decided to write down the directions for installing (even though this one is pretty standard as UNIX packages go).

A few cool things I'm learning about Bigloo:
* A [mostly](http://www-sop.inria.fr/mimosa/fp/Bigloo/bigloo-1.html#Features) [r5rs](http://www.schemers.org/Documents/Standards/R5RS/) compliant Scheme compiler
* Bigloo is a "batch compiler" that includes generating code to C, JVM, or .NET runtimes
* C and Java extension support (Scheme <-> C / Scheme <-> Java) at runtime
* A bunch of [documentation](http://www-sop.inria.fr/mimosa/fp/Bigloo/bigloo-3.html#Documentation), also included in HTML when installing
* GPL license

## Compiling

```
./configure --prefix=$HOME/opt/bigloo-4.2c \
  --jvm=yes \
  --bee=full
make
make test
make compile-bee
make install
make install-bee
cd cigloo/Example; make; ./ctest; cd ../..
```

* `--jvm=yes`: Turns on support for generating Java classes. Requires a JVM and zip utility.
* `--bee=full`: Turns on full support for the included development environment. Includes the binaries cigloo/jigloo.
* `cd cigloo/Example...`: Test Cigloo, which is the

See the included source README/INSTALL for details.

### Issues

* *** ERROR:configure:Can't find zip needed for the JVM back-end

Fix by installing a zip utility, on Debian Jessie: `sudo apt-get install zip`.
