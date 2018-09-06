
# Elm-Open-Iconic

This package has a really easy-to-use API, with plenty of options!

It comes with a stylesheet and icons helpers:
```elm
import OpenIconic
  exposing ( stylesheet
           , wrench
           , accountLogin
           , briefcase
           )

view : model -> Html msg
view _
  = div []
    [ stylesheet
    , wrench
    , accountLogin
    , briefcase
    ]
```


## Customization

This package also has tools for making custom icons:
```elm
import OpenIconic
  exposing ( stylesheet
           , i
           , Icon(Wrench,AccountLogin,Briefcase)
           )

view : model -> Html msg
view _
    = div []
    [ stylesheet
    , i [] Wrench
    , i [] AccountLogin
    , i [] Briefcase
    ]
```


## Elm-Icon Family
- [elm-ionicons](http:/package.elm-lang.org/packages/surprisetalk/elm-ionicons/latest)
- [elm-font-awesome](http:/package.elm-lang.org/packages/surprisetalk/elm-font-awesome/latest)
- [elm-material-icons](http:/package.elm-lang.org/packages/surprisetalk/elm-material-icons/latest)
- [elm-open-iconic](http:/package.elm-lang.org/packages/surprisetalk/elm-open-iconic/latest)

## Contributions
- Feel free to [report bugs on Github](https:/github.com/surprisetalk/elm-open-iconic/issues).
- If you have any suggestions on how to make the API more friendly, please reach out to me at [surprisetalk@gmail.com](mailto:surprisetalk@gmail.com).
