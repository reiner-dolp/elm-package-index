# AnySet

Alternative set implementation for type-safe sets of any type.

This library solves the same problem as [truqu/dictset](https://package.elm-lang.org/packages/truqu/elm-dictset/latest/)
just in a slightly different way. It's built on top of [`any-dict`](https://package.elm-lang.org/packages/turboMaCk/any-dict/latest/)
same way standard Set is implemented on top of standard `Dict`. The only benefit is consistency across the two and
symmetry to core library implementations. In fact, dictset implementation is slightly more optimal since
it's built on top of standard `Dict` implementation and doesn't hold extra unit (`()`) constructor internally.
I encourage you to consider the pros and cons of both before picking one despite I believe that switching between the two should be pretty straightforward if needed.

API mirrors the standard `Set` exactly where possible.

Some parts of the documentation are stolen directly from [`elm-lang/core`](http://package.elm-lang.org/packages/elm-lang/core/latest).
