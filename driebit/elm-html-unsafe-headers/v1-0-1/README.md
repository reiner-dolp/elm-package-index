# Elm-Html-UnsafeHeaders

A library that defines HTML headers with unescaped text.

Whereas the standard headers escape the text (`Html.h1 [] [Html.text "this & that"]` renders as `<h1>this &amp; that</h1>`), these headers do not (`Html.UnsafeHeaders.h1 [] "this & that"` renders as `<h1>this & that</h1>`). The latter is unsafe because if the text is user-generated, then a malicious user can insert any HTML or even JavaScript into a page, so use with care.
