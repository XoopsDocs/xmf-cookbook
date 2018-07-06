# applying

## Metagen::assignTitle\(_$title_\);

Set the page _title_ tag to _$title_.

## Metagen::assignKeywords\(_$keywords_\)

Set the meta _keywords_ tag with using the array of keywords in _$keywords_.

## Metagen::assignDescription\(_$description_\)

Set the meta _description_ tag to _$description_.

## Metagen::generateMetaTags\(_$title_, _$body_\)

Full form:

`Metagen::generateMetaTags(*$title*, *$body*, *$count*, *$minLength*, *$wordCount*, *$forceKeys*)`

Generate and assign title, keywords and description meta tags, taking the title from _$title_, extracting the keywords and description from _$body_.

The maximum number of key words is _$count_, which defaults to 20. Only words at least _$minlen_, which defaults to 4, will be considered.

No more than _$wordCount_ words, default is 100, will be included in the description.

If specified, the array of words in _$forceKeys_ will be used as keywords. Those words will count toward the _$count_.

