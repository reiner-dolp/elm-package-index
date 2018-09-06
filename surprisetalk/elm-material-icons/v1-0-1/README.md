
# Elm-Material-Icons

This package has a really easy-to-use API, with plenty of options!

It comes with a stylesheet and icons helpers:
```elm
import MaterialIcons
  exposing ( stylesheet
           , wrench
           , accountKey
           , briefcase
           )

view : model -> Html msg
view _
  = div []
    [ stylesheet
    , wrench
    , accountKey
    , briefcase
    ]
```


## Customization

This package also has tools for making custom icons:
```elm
import MaterialIcons
  exposing ( stylesheet
           , i
           , Icon(Wrench,AccountKey,Briefcase)
           )

view : model -> Html msg
view _
    = div []
    [ stylesheet
    , i [] Wrench
    , i [] AccountKey
    , i [] Briefcase
    ]
```


### Styling

Some styling shortcuts are included:
```elm
stylishFish : Html Msg
stylishFish
  = i [ light
      , flipV
      , size X48 
      ] 
    Fish
```

The styling helpers are also included as a record:
```elm
stylishFish : Html msg
stylishFish
  = i [ style 
        { shade    = Just Dark
        , inactive = False
        , size     = Just X36
        , flipH    = True
        , flipV    = False
        , rotation = Just Rotate135
        }
      ]
    Fish
```


## Elm-Icon Family
- [elm-ionicons](http:/package.elm-lang.org/packages/surprisetalk/elm-ionicons/latest)
- [elm-font-awesome](http:/package.elm-lang.org/packages/surprisetalk/elm-font-awesome/latest)
- [elm-material-icons](http:/package.elm-lang.org/packages/surprisetalk/elm-material-icons/latest)
- [elm-open-iconic](http:/package.elm-lang.org/packages/surprisetalk/elm-open-iconic/latest)

## Contributions
- Feel free to [report bugs on Github](https:/github.com/surprisetalk/elm-material-icons/issues).
- If you have any suggestions on how to make the API more friendly, please reach out to me at [surprisetalk@gmail.com](mailto:surprisetalk@gmail.com).
