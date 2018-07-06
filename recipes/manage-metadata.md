# Manage Metadata

The [Xmf\Metagen]() class provides methods to extract and summarize content.

While metadata may be best when manually entered, some helpful suggestions through automation could make that process a little smoother.

## SEO Slugs

Using a human meaningful phrase instead of raw id variables in a URL is a common SEO strategy. Most content has a title, and `Xmf\Metagen` has an easy way to turn that title into a slug:

```php
$title = 'xmf - the XOOPS Module Framework';
echo Metagen::generateSeoTitle($title);
```

The output:

> xmf-xoops-module-framework

## Generate Keyword Lists

Given a block of text, `Metagen::generateKeywords()` can extract the most commonly used significant words. Here we feed it the lyrics of "[Mary Had a Little Lamb](http://kids.niehs.nih.gov/games/songs/childrens/maryhad.htm)," asking for a list of four words.

```php
$data = file_get_contents('mary-had-a-little-lamb.txt');
$keywords = \Xmf\Metagen::generateKeywords($data, 4);
echo implode(', ', $keywords);
```

The output:

> mary, lamb, school, play

## Generate a Teaser

Grabbing the lead sentences from a block of text for use as a description is easy. Call `Xmf\Metagen::generateDescription()` with your text and the number of words you want:

```php
$data = file_get_contents('mary-had-a-little-lamb.txt');
$description = \Xmf\Metagen::generateDescription($data, 40);
echo $description;
```

The output:

> Mary had a little lamb, Little lamb, little lamb, Mary had a little lamb, Its fleece was white as snow And everywhere that Mary went, Mary went, Mary went, Everywhere that Mary went The lamb was sure to go...

## Generate a Search Summary

When displaying search results, it is convenient for the user to see a short bit of context that surrounds where the search terms were found in the content. Examining this context helps guide the user to the most relevant results.

Here, we request a summary of about 40 characters, centered around our chosen keyword\(s\), in this case _'school'_. The text breaks on natural boundaries.

```php
$data = file_get_contents('mary-had-a-little-lamb.txt');
$summary = \Xmf\Metagen::getSearchSummary($data, 'school', 40);
echo $summary;
```

The output:

> ...He followed her to school one day...

