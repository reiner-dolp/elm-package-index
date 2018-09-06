# Elm Time Range

Representing time ranges in an elegant manner.

## Example

```elm
module Main exposing (..)

import Html exposing (Html, div, text)
import TimeRange exposing (TimeRange)
import Time exposing (Time)
import Date


main : Html Never
main =
    let
        timeRange =
            TimeRange.fromStartAndEnd
                (toTime
                    "04/17/2017 05:00 PM UTC"
                )
                (toTime
                    "04/17/2017 07:00 PM UTC"
                )
    in
        div []
            [ text (getTimeRangeSummary timeRange)
            ]


getTimeRangeSummary : TimeRange -> String
getTimeRangeSummary timeRange =
    let
        start =
            timeRange
                |> TimeRange.start
                |> Date.fromTime
                |> toString

        end =
            timeRange
                |> TimeRange.end
                |> Date.fromTime
                |> toString

        durationInMinutes =
            timeRange
                |> TimeRange.difference
                |> Time.inMinutes
                |> toString
    in
        "The event starts at "
            ++ start
            ++ " and goes until "
            ++ end
            ++ " and lasts "
            ++ durationInMinutes
            ++ " minutes long"


toTime : String -> Time
toTime dateString =
    dateString
        |> Date.fromString
        |> Result.withDefault (Date.fromTime 0)
        |> Date.toTime

```

## Contributing

I'm happy to recieve any feedback and ideas for additional features. Any input and pull requests are welcome and encouraged!  If you'd like to help or have any ideas, get in touch with me at @ryanolsonx on Twitter or @ryanolsonx on the Elm Slack.
