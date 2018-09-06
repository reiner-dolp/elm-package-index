# For compatibility with [elm-lang/mouse].

The `Mouse` module name is also used in [mpizenberg/elm-pointer-events].
This creates a [compiler error][issue-1625] if both packages are needed.

To circumvent this issue, [elm-lang/mouse] `Mouse` module
is re-exposed here under the `MouseCompat` module name.

[elm-lang/mouse]: http://package.elm-lang.org/packages/elm-lang/mouse/latest
[mpizenberg/elm-pointer-events]: http://package.elm-lang.org/packages/mpizenberg/elm-pointer-events/latest
[issue-1625]: https://github.com/elm-lang/elm-compiler/issues/1625
