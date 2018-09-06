# elm-basscss

A simple attempt to make [Basscss](http://basscss.com/) available in Elm, especially the Elm Reactor.

```elm
import Bass exposing(style, center, h1, italic)


main =
    div
        [ style
            [ center
            , h1
            , italic
            ]
        ]
        [ text "Styled Heading" ]
```

Additional style declarations can be passed in as a list.

```elm
import Bass exposing(style, center, center, italic)


main =
    div
        [ style
            [ center
            , h1
            , italic
            , [ ( "background-color", "red" ) ]
            ]
        ]
        [ text "Styled Heading On Red Background" ]
```

That's it.  So far there is no documentationon for this, except the page you are reading.



Basscss class selectors can be looked up at http://basscss.com/.  Dashes in Basscss selectors become underscores in `Bass.elm`.  Here is an example.

This css rule...

```css
.list-reset{
  list-style:none;
  padding-left:0;
}
```

... looks like this in `Elm.bass`:

```elm
list_reset =
    [ ( "list-style", "none" )
    , ( "padding-left", "0" )
    ]
```

In fact that's all I've done here.  This thing is by no means well engineered.  It's just a hack.  But it allows me to style things like I would in plain HTML.

Media queries and pseudo classes are missing, since they can't be used inline.

Enjoy!
