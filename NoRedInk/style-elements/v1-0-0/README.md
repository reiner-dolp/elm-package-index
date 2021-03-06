# Just a fork to get unstuck for the time being. Don't depend on this...

# The Style Elements Library!

> Join us on the `#style-elements` channel in the [Elm Slack](https://elmlang.herokuapp.com/)!

The Style Elements library is a new set of primitives for working with layout and style in Elm.

The most common goal when working with your view is usually to set or to adjust your layout.

HTML and CSS make this difficult because there's no central place that represents your layout.

You're generally forced to bounce back and forth between multiple definitions in multiple files in order to adjust layout, even though it's pribably the most common thing you'll do.

### Separating Layout and Style

The Style Elements library makes layout a first class idea, which makes working with style and layout a breeze.

It also makes refactoring your style feel similarly invincible as refactoring in Elm!

The main idea is that layout should live in your view, and your stylesheet should deal with all properties _except_ those relating to layout, position, sizing, and spacing.

The `Element` module contains all the components that go in your view.

The `Style` module is the base for creating your stylesheet.
