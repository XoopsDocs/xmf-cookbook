## Highlighter

`Xmf\Highlighter` is a class used to highlight terms in text. It's most common use is highlighting search
terms in content.

### Highlighter::apply(*$words*, *$body*, *$pre*, *$post*)

Apply a highlight to any occurrences of *$words* found in the *$body* text, surrounding each with *$pre* in
front and *$post* behind. Considers only occurrences of words outside of HTML tags.

*$words* is an array of strings to find and highlight. If it is a string, it is treated as a set of space
delimited words and converted to an array of strings.

*$body* is text to which highlight is to be applied.

*$pre* is the markup to be used to start a highlight. By default, it is "<strong>".

*$post* is the markup to be used to start a highlight. By default, it is "</strong>".

The highlighted version of *$body* is returned.
