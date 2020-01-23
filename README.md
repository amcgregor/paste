# [paste.webcore.io](https://paste.webcore.io/)

An anonymous pastebin web application service… just without the "service" part.  Or the "web application".  Intended for reasonable length snippets, with a green light for links that ought to fit within an IRC message.  Utilizes no external assets of any kind, and no "server-side" storage.

For those tiny code samples that happen to be multi-line or require indentation, such as is the case with Python.


### Editing Features

Some functionality beyond standard browser behaviours for a `<textarea>` are included. These assume tab-based indentation. The One True Indentation™.

* **Insertion of literal tabs.**
  This breaks tab-based accessible navigation of the page, but the page is essentially that one input.

* **Multi-line alteration of indentation level.**
  When selecting text across multiple lines, pressing tab (or shift+tab) will increase (or decrease) the indentation level.
  Automatically expands selection to include the full lines from beginning to end.

* **Display of remaining character limit.**
  As the "paste" is contained entirely within the URI, there are hard limits on the upper bound of the storage space available. Additionally, some communications mediums have limits on the length of single unwrapped strings.

  * If the meter is magenta, less than 160 bytes of space have been utilized, and the link is safe to SMS or iMessage.

  * If the meter is green, less than 256 bytes of space have been utilized, and the link is (most likely; depends on your "ident") safe for pasting into IRC.

  * If the meter is yellow, you have exceeded 75% of the limit.

  * If the meter is red, you have exceeded 90% of the limit.


### License

Copyright © 2020 Alice Bevan-McGregor and contributors.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
