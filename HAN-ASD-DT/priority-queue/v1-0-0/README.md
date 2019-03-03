# priority-queue
A priority queue for Elm.

A [*priority queue*][priority-queue] is an

> abstract data type which is like a regular [queue][] or [stack][] data structure, but where additionally each element has a "priority" associated with it. In a priority queue, an element with high priority is served before an element with low priority.

The implementation we provide here is based on Okasaki's *leftist heaps*. See [Purely Functional Data Structures][pfds] for more information.

[priority-queue]: https://en.wikipedia.org/wiki/Priority_queue
[queue]: https://en.wikipedia.org/wiki/Queue_(abstract_data_type)
[stack]: https://en.wikipedia.org/wiki/Stack_(abstract_data_type)
[pfds]: https://www.cs.cmu.edu/~rwh/theses/okasaki.pdf
