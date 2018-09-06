# elm-bem-helpers

Some helpers for using BEM class names that I often use.

## example

```elm
import Html exposing (div, text, br)
import Html.Attributes exposing (class)
import BEMHelpers as BEM
import BEMHelpers.Class as Class


type Block
    = Menu


type Element
    = List_Item
    | Image


type Modifier
    = Active


main =
    div [ Class.b__ Menu ]
        [ div [ Class.be_ Menu Image ]
            [ text (BEM.be_ Menu Image)
            ]
        , div [ Class.b_m Menu Active ]
            [ text (BEM.b_m Menu Active)
            ]
        , div [ Class.bem Menu List_Item Active ]
            [ text (BEM.bem Menu List_Item Active)
            ]
        ]
```
