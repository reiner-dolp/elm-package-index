# Tachyons For Elm

This basically allows [Tachyons](http://tachyons.io/) auto-completion to work in Elm.

See the Tachyons Module on http://package.elm-lang.org/packages/justgage/tachyons-elm/latest for more info.

# Working example

This is the smallest possible program for working with this library.

```elm
module Main exposing (..)

import Tachyons exposing (classes, tachyons)
import Tachyons.Classes exposing (f1, purple, pointer, b)
import Html exposing (..)


main =
    div [ classes [ f1, purple, pointer, b ] ]
        [ tachyons.css
        , text "I'm Purple and big!"
        ]
```



[DEMO HERE](https://ellie-app.com/3P4DBzBNF8Ga1)


# Helping out

I use a JS script to generate my Tachyons classes. To do so as well do the following:

```
npm install
./build.sh
```

This will create `Tachyons/Classes.elm`, format it, and make sure it builds.

### Requirements

* [elm-format](https://github.com/avh4/elm-format) for formatting elm
* [prettier](https://github.com/prettier/prettier) for formatting js. `prettier --write scripts/file_name.js`
