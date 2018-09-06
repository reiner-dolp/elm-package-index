# billstclair/elm-recovered

The [billstclair/elm-recovered](http://package.elm-lang.org/packages/billstclair/elm-recovered/latest) package is for recovering packages that have been removed from GitHub. The basic idea is that you restore the source for the package to your own GitHub repository, but prepend `Recovered.` to all the module names, to keep the recovered package from colliding with multiple inlined copies of the lost code.

This package has only this README file, plus a `Recovered` module.

To add a newly recovered package, modify its source to add the `Recovered.` prefix to all of its module names, `elm package publish` it, then submit a pull request to https://github.com/billstclair/elm-recovered, adding the new package to the list below in this `README.md` file (alphabetical by the package name after the user prefix). I'll take care of bumping the version number and changing `Recovery.elm` to match.

# Recovered Packages

* [billstclair/elm-recovered-utf8](http://package.elm-lang.org/packages/billstclair/elm-recovered-utf8/latest) recovers [spisemisu/elm-utf8](http://package.elm-lang.org/packages/spisemisu/elm-utf8/latest)

Bill St. Clair
27 June, 2018
