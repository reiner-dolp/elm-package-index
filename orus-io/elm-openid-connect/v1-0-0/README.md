# Elm OpenID Connect [![](https://img.shields.io/badge/doc-elm-60b5cc.svg?style=flat-square)](http://package.elm-lang.org/packages/orus-io/elm-openid-connect/latest)


This package offers some utilities to implement a client-side
[OpenID Connect]() authentication in Elm. It covers only
the 'Implicit' grant type.

The design is heavily based on [truqu/elm-oauth2](https://github.com/truqu/elm-oauth2),
on which it will probably depend in a later version.

## Getting Started

### Installation

```bash
elm package install orus-io/elm-openid-connect
```

### Usage

#### Imports

```elm
import OpenIDConnect
import OpenIDConnect.Decode
```

#### Authorization

```elm
update : Msg -> Model -> ( Model, Cmd Msg )
update msg model =
    case msg of
        NoOp ->
            model ! []

        Authorize ->
            model
                ! [ OpenIDConnect.newAuth "authorizationEndpoint" "redirectUri" "clientId"
                    |> withScope []  -- optional extra scope
                    |> withState []  -- optional state
                    |> OpenIDConnect.authorize
                  ]
```

#### Parsing the token

```elm
init : Navigation.Location -> ( Model, Cmd Msg )
init location =
    let
        model = {}
    in
        case OpenIDConnect.parse location of
            -- A token has been parsed 
            Ok token ->
                { model | token = Just token } ! []

            -- Nothing to parse, unauthenticated
            Err OpenIDConnect.NoToken ->
                model ! []

            -- An other type of error (invalid parsing or an actual OAuth error) 
            Err _ ->
                model ! []
```

#### Using the token

```elm
let
    req =
        Http.request
            { method = "GET"
            , body = Http.emptyBody
            , headers = OpenIDConnect.use token [] -- Add the token to the http headers
            , withCredentials = False
            , url = "whatever"
            , expect = Http.expectJson decoder
            , timeout = Nothing
            }
in
    { model | token = Just token } ! [ Http.send handleResponse req ]
```


