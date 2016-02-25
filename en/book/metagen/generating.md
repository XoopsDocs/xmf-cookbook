## Generating Metadata

### Metagen::generateKeywords(*$body*, *$count*, *$minLength*, *$forceKeys*)

Extract a list of keywords from the text *$body*.

The maximum number of key words is *$count*, which defaults to 20.
Only words at least *$minlen*, which defaults to 4, will be considered.

If specified, the array of words in *$forceKeys* will be used as keywords. Those words will count
toward the *$count*.

Return array of keywords.

## Metagen::generateDescription(*$body*, *$wordCount*)

Extract a short description from the text *$body*.

No more than *$wordCount* words, default is 100, will be included in the description.

Returns a string.

## Metagen::generateSeoTitle(*$title*, *$extension*)

Create an SEO slug from the *$title*, adding the string *$extension*, if specified.

## Metagen::getSearchSummary(*$haystack*, *$needles*, *$length*)

Splits a string, *$haystack*, into a string no longer than the length specified as *$length*, default 120.
The string is centered around the first occurrence of any string in the array *$needles*, or starting
at the beginning of the string if no *$needles* are specified or found.

## Metagen::checkStopWords(*$key*)

Look up the word *$key* in the list of [stop words](https://en.wikipedia.org/wiki/Stop_words) and
classify it as a significant word or a stop word.

Returns *true* if the word is significant, or *false* if it is a stop word,

