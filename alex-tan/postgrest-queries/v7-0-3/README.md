# alex-tan/postgrest-queries

[![Build Status](https://travis-ci.org/alex-tan/postgrest-queries.svg?branch=master)](https://travis-ci.org/alex-tan/postgrest-queries)

This package allows you to easily construct [Postgrest query strings](http://postgrest.org/en/v5.1/api.html#horizontal-filtering-rows) using Elm.

Most query operators are currently supported:

* [select](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#select)
* [eq](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#eq)
* [gt](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#gt)
* [gte](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#gte)
* [lt](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#lt)
* [lte](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#lte)
* [neq](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#neq)
* [like](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#like)
* [ilike](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#ilike)
* [in](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#inList)
* [is.null](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#null)
* [is.true](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#true)
* [is.false](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#false)
* [fts](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#fts)
* [plfts](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#plfts)
* [phfts](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#plfts)
* [not](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries#not)

[View Full Documentation](https://package.elm-lang.org/packages/alex-tan/postgrest-queries/latest/Postgrest-Queries)


## Using `select`


If you're not selecting any nested resources in your request, you can use `attributes`:

```elm
-- "select=id,name"
P.toQueryString
    [ P.select <| P.attributes [ "id", "name" ]
    ]
```

If you want to select attributes and resources, you can use the `attribute` and `resource` functions:

```elm
-- select=id,name,grades(percentage)
P.toQueryString
  [ P.select
      [ P.attribute "id"
      , P.attribute "name"
      , P.resource "grades"
          [ P.attribute "percentage"
          ]
      ]
  ]
```

The library also provides a nice abstraction that allows you to both specify nested resources in a select clause, as well as use other postgrest parameters on those nested resources such as `order`, `limit`, and all of the usual conditional parameters such as `eq`:


```elm
-- select=id,name,grades(percentage)&grades.order=percentage.desc&grades.limit=10
P.toQueryString
  [ P.select
      [ P.attribute "id"
      , P.attribute "name"
      , P.resourceWithParams "grades"
          [ P.order [ P.desc "percentage" ], P.limit 10 ]
          [ P.attribute "percentage"
          ]
      ]
  ]
```

## Conditions

The library currently supports the most commonly used query parameters. Here's a sampling of how they can be used in combination with one another:

```elm
-- student_id=eq.100&grade=gte.90&or=(self_evaluation.gte.90,self_evaluation.is.null)
P.toQueryString
  [ P.param "student_id" <| P.eq <| P.int 100
  , P.param "grade" <| P.gte <| P.int 90
  , P.or
      [ P.param "self_evaluation" <| P.gte <| P.int 90
      , P.param "self_evaluation" P.null
      ]
  ]
```

The `in` operator can be used with `inList`. The second parameter is a list of whatever values you're using in your app and the first argument is the function that will transform the items in that list into the library's `Value` type such as `string` or `int`.

```elm
-- name=in.("Chico","Harpo","Groucho")
P.toQueryString
  [ P.param "name" <| P.inList P.string [ "Chico", "Harpo", "Groucho" ]
  ]
```

## Order

You can order results by multiple columns as well as using `nullsfirst` or `nullslast`.

```elm
-- order=age.asc.nullsfirst,created_at.desc
P.toQueryString
  [ P.order
      [ P.asc "age" |> P.nullsfirst
      , P.desc "created_at"
      ]
  ]
```

## Combining Params

Maybe you have default parameters that you want to reuse across multiple functions. You can combine them using `combineParams`:

```elm
defaultParams : P.Params
defaultParams =
    [ P.select <| P.attributes [ "id", "name" ]
    , P.limit 10
    ]


constructParams : P.Params -> P.Params
constructParams =
    P.combineParams defaultParams


-- limit=100&select=id,name
constructParams [ P.limit 100 ]
```

Note that the merging of the two sets is not recursive. The two are merged by the final query parameter name such as `order` or `children.order`, etc... and the second set's value is always preferred.