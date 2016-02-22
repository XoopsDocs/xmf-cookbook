## Generating Metadata

### Metagen::generateKeywords(string $body, integer $count = 20, integer $minLength = 4, string[]|null $forceKeys = null  )

generateKeywords builds a set of keywords from text body

## Metagen::generateDescription(string $body, integer $wordCount = 100 ) 

generateDescription - generate a short description from a body of text

## Metagen::generateSeoTitle(string $title = '', string $extension = '' )

Create a title for the short_url field of an article

## Metagen::getSearchSummary(string $haystack, mixed $needles = null, integer $length = 120 )

getSearchSummary splits a string into string no larger than a specified length, and centered around the first occurrence of any of an array of needles, or starting at the beginning of the string if no needles are specified or found.

## Metagen::checkStopWords(string $key )

checkStopWords - look up a word in a list of stop words and classify it as a significant word or a stop word.
https://en.wikipedia.org/wiki/Stop_words
