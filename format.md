What should the database format be?

CSV?  Turtle?  JSON-LD?  RDF/XML?

How about markdown?

Specifically:

* Each term is a level-1 heading, and the text until the next heading (or end of file) is the data for that item
* Definition starts with a markdown table which is the structured data, and then the rest of the data is the spec (which gets turned into HTML by a markdown processor).

For example:

> # replies
>
> [replies]: #replies
>
> Property| Value 
> --------|:----- 
> domain  | [Object]
> range   | [Collection]
> func    | true
> status  | stable
> editor  | evanp, jasnell
> impls   | <https://www.w3.org/2017/02/social/implementations/as2/>
> tests   | <https://github.com/w3c/activitystreams/tree/master/test>
>
> Identifies a [Collection] containing objects considered to be responses to this object.
> 
> Example:
>
> 
> ```json
> {
>   "@context": "https://www.w3.org/ns/activitystreams",
>   "summary": "A simple note",
>   "type": "Note",
>   "id": "http://www.test.example/notes/1",
>   "content": "I am fine.",
>   "replies": {
>     "type": "Collection",
>     "totalItems": 1,
>     "items": [
>       {
>         "summary": "A response to the note",
>         "type": "Note",
>         "content": "I am glad to hear it.",
>         "inReplyTo": "http://www.test.example/notes/1"
>       }
>     ]
>   }
> }
> ```

To make the links work trivially using square brackets, terms should also define themselves as markdown footnote-references, using the ```[foo]: #foo``` syntax.  We could also do that with editors, etc.

So the markdown looks like:

```markdown
# replies

[replies]: #replies

Property| Value 
--------|:----- 
domain  | [Object]
range   | [Collection]
func    | True
status  | "stable"
editor  | evanp, jasnell
impls   | <https://www.w3.org/2017/02/social/implementations/as2/>
tests   | <https://github.com/w3c/activitystreams/tree/master/test>

Identifies a [Collection] containing objects considered to be responses to this object.
 
Example:

...
```

[replies]: #replies
[Object]: #Object
[Collection]: #Collection

## Issue: Ordering and Grouping

What order should they be kept in?  Alphabetic?  Grouped by subject?  Time order?

We could also allow multiple different files, for even easier grouping by subject.  Could be a table at the top of the file for default values of properties of all the entries in the file!   Then an "extension" is probably a file.

The cross-term links wouldn't work until all the files were concatenated, but that's probably okay.

