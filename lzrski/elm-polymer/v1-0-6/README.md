# Elm Polymer

Elm bindings to some of the [PolymerElements Web Components][PolymerElements].

> Warning: This is an experiment on a rather early stage.

## Install

```sh
elm-package install lzrski/elm-polymer
```

You also need to link Polymer web components bundle in your HTML:

```html
<link rel="import" href="https://cdn.rawgit.com/lzrski/elm-polymer/1.0.0/assets/web-components-bundle.html">
```

If you don't want to use CDN you can also download it. It's just this one file.

## Use

Import some modules and start playing with it:


```elm
import Polymer.Paper.IconButton exposing (iconButton)
import Polymer.Paper.IconButton.Attributes exposing (icon)

view model =
  iconButton [ icon "menu" ] [ ]
```

Here! You have a one-button app :P

You may find it beneficial for the experience to also add following markup to your HTML's head':

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
<link
  rel="stylesheet"
  type="text/css"
  href="//fonts.googleapis.com/css?family=Roboto:400,300,500|Roboto+Mono|Roboto+Condensed:400,700&subset=latin,latin-ext"
/>
<style>
  html, body {
    width: 100%;
    height: 100%;
    padding: 0;
    margin: 0;
    font-family: 'Roboto', 'Noto', sans-serif;
    font-weight: normal;
    font-size: 14px;
    -webkit-font-smoothing: antialiased;
  }
</style>
```

## Idea

Most of the code is generated by processing data exposed at https://www.webcomponents.org/api

See [scripts/scaffold](./scripts/scaffold) for some hairy shell scripting that seems to actually work 👹

Once scaffolded the code can be manually edited. It isn't my intention to use this generation forever. Just to get it going.

Big thanks to @edvail for his prior implementation of [elm-polymer](/edvail/elm-polymer/) and @rtfeldman's [Elm Google Map example](rtfeldman/elm-google-maps) for inspiration.

## Contributing

If you want to contribute (please do!) here is how to use local copy of this library in your app.

1.  Clone this repository.

2.  Soft-link `src/Polymer` to your app's `src/`, e.g.:

    ```sh
    ln -s ../../elm-polymer/src/Polymer src/
    ```

Now you may make changes to the library and your app should pick them up on next build. If the changes are useful, please share back via PR.

[PolymerElements]: https://www.webcomponents.org/author/PolymerElements