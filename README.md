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


### Frequently Asked Questions / Comments

* **Why don't you just Base64 encode and use that?**
  
  > &lt;tappi&gt;
  > could've at least base64 encoded it so you wouldn't be literally pasting the code just in query params
  > kinda misses the point of paste services if you're still pasting the code
  
  Because Base64-encoding actually makes the result larger. Instead of having three characters to encode one, occasionally, you have a _minimum_ of two characters per encoded character, always, _plus padding_. For even short snippets, this can have a significant impact.
  
  Additionally, Unless you are truly a savant, Base64 entirely obscures the content… for no gain.  Compare the following:
  
  **148 bytes, Base64:** `aW1wb3J0IHN5cwoKZGVmIG1haW4oeCwgeSk6CglyZXR1cm4gaW50KHgpICogaW50KHkpCgppZiBfX25hbWVfXyA9PSAnX19tYWluX18nOiBzeXMuZXhpdChtYWluKCpzeXMuYXJndlsxOl0pKQ==`

  **125 bytes, URL encoded:** `import+sys%0A%0Adef+main(x,+y):%0A%09return+int(x)+*+int(y)%0A%0Aif+__name__+==+%27__main__%27:+sys.exit(main(*sys.argv[1:]))`

  Bonus, it's still readable! The entire suggestion to use Base64 avoids the point of this "service" as a response to users writing their questions into paste services, pasting the link, then just hoping someone's curious enough to click it.  [The link is the question.](https://paste.webcore.io/?This+resolves+my+complaint+of+people+using+Paste+services+to+ask+questions,+though.++The+link+is+the+question.)


### License

Copyright © 2020 Alice Bevan-McGregor and contributors.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
