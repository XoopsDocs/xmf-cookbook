# Highlighter

`Xmf\Highlighter` is a class used to highlight terms in text. It's most common use is highlighting search terms in content.

## Highlighter::apply\(_$words_, _$body_, _$pre_, _$post_\)

Apply a highlight to any occurrences of _$words_ found in the _$body_ text, surrounding each with _$pre_ in front and _$post_ behind. Considers only occurrences of words outside of HTML tags.

_$words_ is an array of strings to find and highlight. If it is a string, it is treated as a set of space delimited words and converted to an array of strings.

_$body_ is text to which highlight is to be applied.

_$pre_ is the markup to be used to start a highlight. By default, it is "".

_$post_ is the markup to be used to start a highlight. By default, it is "&lt;/strong&gt;".

The highlighted version of _$body_ is returned.

