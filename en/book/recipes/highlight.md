## Highlight Content

There are times when you may want to highlight certain words within your module page.
One common use is to guide the user to occurrences of search terms in the display body.
For this example, we assume you have an array of terms to highlight in *$words*, and
some text (HTML is fine) in *$body*.

```php
$pre = '<span class=”highlight”>';
$post = '</span>';
\Xmf\Highlighter::apply($words, $body, $pre, $post);
```

Each occurrence of $words in $body will be surrounded by $pre and $post.
If you do not specify the *$pre* and *$post* arguments, the terms will be surrounded
by `<strong>` and  `</strong>` tags.
