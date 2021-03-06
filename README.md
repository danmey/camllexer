Camllexer is an enhanced lexer for Caml dialects.

The lexer has been extracted from the Camlp4 (> 3.10) lexer, which in turns
was reimplemented as a derivative of the lexer from the OCaml compiler.

This lexer has the following particularities:

* Correct and complete: as far as testing gone (~800\_000 distinct
  lines over ~3\_000\_000 lines of Caml like files).
* Supports most Caml dialects:
  * By re-using the lexer of Camlp4 this lexer works on any
    extension of the OCaml language made with Camlp4.
    In particular it has a support for quotations and anti-quotations.
  * Works fine on lexers and parsers (ocamllex, ocamlyacc),
    except when using the C style of comments.
* Lossless: every single bit of the input file is kept.
  Blanks, comments, newlines, lexical conventions for writing
  literals, all of it is kept in the returned token stream.
  Undesired information can easily be thrown out of the stream.
* Keyword independent: there is no token for keywords. This
  is up to you to cast some LIDENTs and some SYMBOLs into
  proper keyword tokens of your own token type.
* Fault tolerant: errors take part of the token stream, allowing
  to write fault tolerant translations.
* Flexible warnings: the lexer warn about some corner case of
  the lexical conventions that the user might want to avoid, again
  warnings take part of the token stream such that you easily
  control everything.
* A simple lexer program is provided, it enables quick debugging,
  and simple stream editions using Unix pipelines!
