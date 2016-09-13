---
layout: post
title: Lisp1 and Bigloo
category: Compilers
tags: ['Scheme', 'Bigloo']
published: false
---

After taking the time to get a full installation of [Bigloo](http://www-sop.inria.fr/mimosa/fp/Bigloo/bigloo.html) I ended up reading parts of the manual, which made it pretty obvious how to get a [Lisp1 implementation](https://github.com/gmunoz/lisp/blob/master/1.4.scm) from *Lisp in Small Pieces* running. All I had to do was add the following code to my code listing:
```scheme
(module chapter1
	(main start))

(define (start argv)
  (chapter1-scheme)
  (newline))
```

Bigloo wants to compile module instead of whole programs. Thus, all that's needed is a module declaration to get object code: `bigloo -c 1.4.scm`.

The second part is Bigloo's version of an entry point into an application. Adding that so that it invokes the read-eval-print loop of the interpreter when running the executable that Bigloo creates when compiling the program: `bigloo 1.4.scm`.
