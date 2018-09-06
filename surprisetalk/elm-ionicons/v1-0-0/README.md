
# Elm-Ionicons

This package has a really easy-to-use API, with plenty of options!

It comes with a stylesheet and icons helpers:
```elm
import Ionicons
  exposing ( stylesheet
           , wrench
           , pieGraph
           , briefcase
           )

view : model -> Html msg
view _
  = div []
    [ stylesheet
    , wrench
    , pieGraph
    , briefcase
    ]
```


## Customization

This package also has tools for making custom icons:
```elm
import Ionicons
  exposing ( stylesheet
           , i
           , Icon(Wrench,PieGraph,Briefcase)
           )

view : model -> Html msg
view _
    = div []
    [ stylesheet
    , i [] Wrench
    , i [] PieGraph
    , i [] Briefcase
    ]
```


## Elm-Icon Family
- [elm-ionicons](http:/package.elm-lang.org/packages/surprisetalk/elm-ionicons/latest)
- [elm-font-awesome](http:/package.elm-lang.org/packages/surprisetalk/elm-font-awesome/latest)
- [elm-material-icons](http:/package.elm-lang.org/packages/surprisetalk/elm-material-icons/latest)
- [elm-open-iconic](http:/package.elm-lang.org/packages/surprisetalk/elm-open-iconic/latest)

## Contributions
- Feel free to [report bugs on Github](https:/github.com/surprisetalk/elm-ionicons/issues).
- If you have any suggestions on how to make the API more friendly, please reach out to me at [surprisetalk@gmail.com](mailto:surprisetalk@gmail.com).
