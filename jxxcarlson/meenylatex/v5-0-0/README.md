
MeenyLaTeX
=========

MeenyLaTeX is an experimental version of the MiniLatex
package.


MiniLatex (the language) is a subset of LaTeX that can be rendered
into pdf by standard tools such as `pdflatex`.  MiniLatex source
text can be live-rendered in a web browser using a suitable application, e.g.,
[MiniLatex Live](https://jxxcarlson.github.io/app/miniLatexLive/index.htmll)
or [www.knode.io](http://www.knode.io).  For a technical discussion,
see the Hackernoon article, [Towards LaTeX in the Browser](https://hackernoon.com/towards-latex-in-the-browser-2ff4d94a0c08).


Changes
-------

0. The top level module `Driver` has been renamed `MiniLatex`

1. MiniLatex renders LaTeX source text into `Html a` using
`Render2.render` rather than
`String` representing Html using `Render.render`

2. The `MiniLatex` module uses the `Html a` renderer as does the demo app.  

3.  MathJax is called to render formulas using custom elements 
(courtesy of @luke on the Elm Slack), rather than using ports.

I plan to re-expose the `String` renderer in the `MiniLatex` module.
This is needed for printing and can also be used to publish documents
as Html using a different frontend.

*Note:*  Since this is the experimental version,
the API may change (and be cleaned up) substantially.  
I've exposed much more than is eventually needed 
in order to experiment better.



Note to myself
--------------
On my laptop, this repository is in /Users/carlson/dev/apps/MiniLatex/MeenyLatexPackage2


Acknowledgments
---------------  

I wish to acknowledge the generous help that I have received throughout this project from the community at http://elmlang.slack.com, with special thanks to Ilias van Peer (@ilias), Luke Westby (@luke), and
Evan Czaplicki (@evancz).
