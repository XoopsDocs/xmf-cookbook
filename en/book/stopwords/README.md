## Stop Words

`Xmf\StopWords` is used to check if a given word is considered a 
[stop word](https://en.wikipedia.org/wiki/Stop_words).

Stop words are words which are filtered out during processing of text data.
An example use case is [Metagen::generateKeywords()](../metagen/generating.md), 
which eliminates stop words from the list of potential keywords. 

## Basic Usage

### $stopwords = new StopWords()

Creates a new StopWords object that containes the stop word list for the current language.

### check(*$key*)

Look up the word *$key* in the list of stop words and classify it as a significant word or a stop word.

Returns *true* if the word is significant, or *false* if it is a stop word.
