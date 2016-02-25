## Applying Metadata to an HTML document

### Metagen::assignTitle(*$title*);

Set the page *title* tag to *$title*.

### Metagen::assignKeywords(*$keywords*)

Set the meta *keywords* tag with using the array of keywords in *$keywords*.


### Metagen::assignDescription(*$description*)

Set the meta *description* tag to *$description*.

### Metagen::generateMetaTags(*$title*, *$body*)

Full form:

`Metagen::generateMetaTags(*$title*, *$body*, *$count*, *$minLength*, *$wordCount*, *$forceKeys*)`

Generate and assign title, keywords and description meta tags, taking the title from *$title*, extracting
the keywords and description from *$body*.

The maximum number of key words is *$count*, which defaults to 20.
Only words at least *$minlen*, which defaults to 4, will be considered.

No more than *$wordCount* words, default is 100, will be included in the description.

If specified, the array of words in *$forceKeys* will be used as keywords. Those words will count
toward the *$count*.


