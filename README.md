# [paste.webcore.io](https://paste.webcore.io/)

An anonymous "pastebin"-like web application service… just without the "service" part.  Or the "web application", and without permanent storage.  Intended for reasonable length snippets, ones that typically would fit reasonably within a chat input box, but where fixed-width formatting must be preserved. Provides a "remaining character counter" and currently enforces a 4KB upper limit, is built of **absolutely minimal** HTML5, CSS, and ES6, delivered as a single file with no external assets or requests of any kind.

For those tiny code samples that happen to be multi-line or require indentation, such as is the case with Python, and for which permanent storage / tracking would be essentially a pointless waste of resources.

Why? Because [I'm Batman](https://paste.webcore.io/?+++++++++.++.%0A++++++++++%7C%5C_%7C%5C%0A++++++++++%7C+a_a%5C++%22Because+I%27m+Batman.%22%0A++++++++++%7C+%7C+%22]%0A++++++____%7C+%27-%5C___%0A+++++%2F.----.___.-%27%5C%0A++++%2F%2F++++++++_++++%5C%0A+++%2F%2F+++.-.+%28~v~%29+%2F%7C%0A++%7C%27%7C++%2F%5C:++.--++%2F+%5C%0A+%2F%2F+%7C-%2F++%5C_%2F____%2F%5C%2F~%7C%0A%7C%2F++%5C+%7C++[]_%7C_%7C_]+%5C+%7C%0A%7C+%5C++%7C+%5C+%7C___+++_%5C+]_}%0A%7C+%7C++%27-%27+%2F+++%27.%27++%7C%0A%7C+%7C+++++%2F++++%2F%7C:++%7C+%0A%7C+%7C+++++%7C+++%2F+%7C:++%2F%5C%0A%7C+%7C+++++%2F++%2F++%7C++%2F++%5C%0A%7C+%7C++++%7C++%2F++%2F++%7C++++%5C%0A%5C+%7C++++%7C%2F%5C%2F++%7C%2F%7C%2F%5C++++%5C%0A+%5C%7C%5C+%7C%5C%7C++%7C++%7C+%2F+%2F%5C%2F%5C__%5C%0A++%5C+%5C%7C+%7C+%2F+++%7C+%7C__%0Asnd++++%2F+%7C+++%7C____%29%0A+++++++%7C_%2F). Because [some languages demand sensible indentation](https://paste.webcore.io/?import+sys%0A%0Adef+main%28x:str,+y:str%29+-%3E+int:%0A%09return+int%28x%29+*+int%28y%29%0A%0Aif+__name__+==+%27__main__%27:+sys.exit%28main%28*sys.argv[1:]%29%29) — and that link totally fits in an IRC message, showing a typical "main application script" structure, **in its entirety**. Almost all languages [just look better](https://paste.webcore.io/?%27use+strict%27;%0A%0Aconst+SAFE+=+%7B%0A%09%09paranoid:+false,%0A%09%09%2F%2F+...%0A%09}%0A%0Afunction+commit%28origin%29+%7B%0A%09let+value+=+origin.value,%0A%09%09safe+=+SAFE[representation.value]++%2F%2F+Where+is+this+coming+from%3F+👹%0A%09%0A%09%2F%2F+...%0A%7D).


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

* **Is this actually an April Fool's joke?**
  
  Sadly, no. Too many users were entering IRC channels I moderate or participate heavily in, only to paste a link without the faintest whiff of romance first. Some would ask some form of question surrounding what they think they've shared, others would leave it at that. In both scenarios, often those users would eventually become upset when their answer receives no attention.
  
  In many cases, such as is the case with the developer of this "service", corporate firewall/gateway policies prevent access to anonymous file uploading/sharing services (protection against malware exfiltration of corporate secrets), block access to truly anonymous services as they are frequently utilized for botnet command and control (C&amp;C), and block access to services which permit upload of user content which is then delivered anonymously with the correct MIME-type, e.g. permitting upload and execution of remote JavaScript.
  
  According to one CTO, "there exists no legitimate reason to permit access to these services in the face of the threat they represent to corporate IP and infrastructure".

* **Why don't you just Base64 encode and use that?**
  
  > &lt;tappi&gt;
  > could've at least base64 encoded it so you wouldn't be literally pasting the code just in query params
  > kinda misses the point of paste services if you're still pasting the code
  
  Because Base64-encoding actually makes the result larger. Instead of having three characters to encode one, occasionally, you have a _minimum_ of two characters per encoded character, always, _plus padding_. For even short snippets, this can have a significant impact.
  
  Additionally, unless you are truly a savant, Base64 entirely obscures the content… for no gain.  Compare the following:

  <details open><summary><strong>148 bytes, Base64</strong></summary>
  
  ```
  aW1wb3J0IHN5cwoKZGVmIG1haW4oeCwgeSk6CglyZXR1cm4gaW50KHgpICogaW50KHkpCgppZiBfX25hbWVfXyA9PSAnX19tYWluX18nOiBzeXMuZXhpdChtYWluKCpzeXMuYXJndlsxOl0pKQ==
  ```
  </details>

  <details open><summary><strong>125 bytes, URL encoded</strong></summary>
  
  ```
  import+sys%0A%0Adef+main(x,+y):%0A%09return+int(x)+*+int(y)%0A%0Aif+__name__+==+%27__main__%27:+sys.exit(main(*sys.argv[1:]))
  ```
  </details>

  Bonus, it's still readable! The entire suggestion to use Base64 avoids the point of this "service" as a response to users writing their questions into paste services, pasting the link, then just hoping someone's curious enough to click it.  [The link is the question.](https://paste.webcore.io/?This+resolves+my+complaint+of+people+using+Paste+services+to+ask+questions,+though.++The+link+is+the+question.)


### License

Copyright © 2020 Alice Bevan-McGregor and contributors.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
