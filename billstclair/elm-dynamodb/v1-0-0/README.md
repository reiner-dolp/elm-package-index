# billstclair/elm-dynamodb

Elm Interface to [Amazon DynamoDB](https://aws.amazon.com/dynamodb/).

You can run your code against a pure Elm simulator during development, and then change the initial value of the "database" parameter to switch to the real Amazon backend.

[examples/src/simulated.elm](examples/src/simulated.elm) is an example application that uses the simulator. See the REAME in [examples/](examples/) for instructions on running it in `elm-reactor`. It is live at [kakuro-dojo.com/simulated.html](https://kakuro-dojo.com/simulated.html).

[examples/src/real.elm](examples/src/real.elm) is an example application that uses the real backend. It is live at [kakuro-dojo.com/dynamo-example.html](https://kakuro-dojo.com/dynamo-example.html).

Both are tiny wrappers around [examples/src/SharedUI.elm](examples/src/SharedUI.elm).

The library itself is in [src/DynamoBackend.elm](src/DynamoBackend.elm).

It takes some configuration to make the real backend ports work on your own site with your own DynamoDB table. The process of creating the backend table on Amazon's web site is documented in [Configuring Amazon DynamoDB for DynamoBackend](amazon-setup.md). Hooking the Elm port JavaScript into your code is documented in [Using the DynamoBackend JavaScript](port-setup.md).

Bill St. Clair &lt;billstclair@gmail.com&gt;<br/>
12 November 2016
