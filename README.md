predicates
==========

A racket package for creating predicates in a point-free style. [Documentation](http://pkg-build.racket-lang.org/doc/predicates/index.html)

A *predicate* is a function that takes one argument and returns either true or false. You can think of it as a question, such as `even?` which returns true for even numbers and false for odd numbers. This package provides several tools for working with predicates.

Predicates can be combined logically

```racket
(filter (or? symbol? string?) '(1 a 3 "blah" b 4 5))
; -> '(a "blah" b)

(filter (and? number? even?) '(a b 2 5 6 "foo" bar 9 8))
; -> '(2 6 8)

(filter (not? symbol?) '(a b 2 3 "baz" d))
; -> '(2 3 "baz")
```

Predicates can be constructed for comparisons

```racket
(filter (<? 5) '(3 4 5 6 7))
; -> '(3 4)
(filter (eq?? 'foo) '(foo bar baz))
; -> '(foo)
(define digit? (and? exact-positive-integer? (<? 10)))
(filter digit? '(a b 2 5 c "foo" 12 15 8))
; -> '(2 5 8)
```
