# generating

## Generating Metadata

### Metagen::generateKeywords\(_$body_, _$count_, _$minLength_, _$forceKeys_\)

Extract a list of keywords from the text _$body_.

The maximum number of key words is _$count_, which defaults to 20. Only words at least _$minlen_, which defaults to 4, will be considered.

If specified, the array of words in _$forceKeys_ will be used as keywords. Those words will count toward the _$count_.

Return array of keywords.

## Metagen::generateDescription\(_$body_, _$wordCount_\)

Extract a short description from the text _$body_.

No more than _$wordCount_ words, default is 100, will be included in the description.

Returns a string.

## Metagen::generateSeoTitle\(_$title_, _$extension_\)

Create an SEO slug from the _$title_, adding the string _$extension_, if specified.

## Metagen::getSearchSummary\(_$haystack_, _$needles_, _$length_\)

Splits a string, _$haystack_, into a string no longer than the length specified as _$length_, default 120. The string is centered around the first occurrence of any string in the array _$needles_, or starting at the beginning of the string if no _$needles_ are specified or found.

## Metagen::checkStopWords\(_$key_\)

 **This method is deprecated. Use of** [**StopWords::check\(\)**](../stopwords.md) **is prefered.**

Look up the word _$key_ in the list of [stop words](https://en.wikipedia.org/wiki/Stop_words) and classify it as a significant word or a stop word.

Returns _true_ if the word is significant, or _false_ if it is a stop word.

