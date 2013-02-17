vminpoly
========

A polyfill for CSS units vw, vh &amp; vmin.

This is a working proof of concept right now. There's a lot of cleanup to do on the code.

Since most browsers ignore rules they don't understand, the code must load and parse the original CSS sourcecode. Once this is done, it filters the generated tree leaving only rules that use 'vh', 'vw' & 'vmin' units.
At window resize time, it generates CSS code for the 'px' equivalents and appends it to the end of the 'head' element, the generated code respects media queries.

As it is, it's fast enough for a lot of cases, but the code can still be optimized greatly, both in parsing and in resizing.

Also, any suggestions on how to better organize the repo, specially with respect to third party code, is greatly appreciated.

TODO:
-----

* Add feature detection, at the moment it's doing it's stuff even in browsers that support the units.
* IE9 and IE10 support vw, vh & vm, so the code should only translate 'vmin' units to 'vm'
* Only linked stylesheets are being parsed right now but it's very easy to also parse 'style' elements.
* tokenizer.js fails in IE8, so no luck there and I presume in earlier IEs for now. It's working fine in IE9, Firefox and Opera, which doesn't support any of the units.