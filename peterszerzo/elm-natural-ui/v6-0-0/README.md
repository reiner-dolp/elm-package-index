# NaturalUi

Opinionated design system with a friendly API.

## Getting started

`elm-package install peterszerzo/elm-natural-ui`

Render your first natural button:

```elm
module Simplest exposing (..)

import NaturalUi as N


main =
    N.button
        [ N.label "Click me"
        , N.warning
        ]
```

Natural UI's views work similar to `elm-lang/html` ones, with custom props that encode shared styling and behavioral patterns shared between components. Here are a few more examples:
* theming: `N.warning`, `N.error`
* additional UI elements: `N.help "Some text for a help tooltip"`, `N.label "Label for your form field"`
* inlets for raw HTML stuff: `N.children`, `N.htmlAttrs`, `N.inputHtmlAttrs`

Not all of these props are available for all components, and some more comprehensive documentation is in order here. In the meantime, you need to look at individual implementations to see what is supported. And keep those issues coming!

## Complex components

Components like `ListEditor` and `SmartTable` handle sortability, autocomplete and a bunch of other things, all while maintaining a separation between input data they operate and change, and purely UI-related internal state such as popup openness or sort order. `Natural UI` does something similar to [elm-sortable-table](http://package.elm-lang.org/packages/evancz/elm-sortable-table/1.0.1/Table):

```elm
module Simple exposing (..)

import Html exposing (Html, div, beginnerProgram)
import NaturalUi as N
import NaturalUi.ListEditor as ListEditor


type alias Model =
    { list : List String
    , editorState : ListEditor.State
    }


model : Model
model =
    { list = [ "A", "list", "to", "be", "edited" ]
    , editorState = ListEditor.init
    }


type Msg
    = ListEditorMsg ListEditor.State ListEditor.Data


update : Msg -> Model -> Model
update msg model =
    case msg of
        ListEditorMsg state data ->
            { model | list = data, editorState = state }


view : Model -> Html Msg
view model =
    N.listEditor
        [ N.data model.list
        , N.state model.editorState
        , N.toMsg ListEditorMsg
        ]


main : Program Never Model Msg
main =
    beginnerProgram
        { model = model
        , update = update
        , view = view
        }
```

The API remains largely the same as before, it's just that now, custom type definitions and data structures are in place to accommodate custom components. `Natural UI` encourages strong separation between `data` and `state`, the former of which is dead simple and exposed (listeditor edits a list of strings, and that's that), the latter precise and fully encapsulated.

## Roadmap

* [x] flush out high-level API, per [elm-sortable-table](https://github.com/evancz/elm-sortable-table)
* [ ] flush out API in detail
* [ ] upgrade to `elm-css@13` (currently on `@9`, with union type class names and stylesheet generation)
* [ ] better docs and guides
