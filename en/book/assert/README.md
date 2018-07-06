# README

The `Xmf\Assert` class offers methods to assert that a PHP variable conforms to your expectations. If the value does not conform, the assertion will throw an `\InvalidArgumentException` that your program can catch and process as appropriate. The exception will include a message that describes the failed assertion. You can easily customize that message if needed.

It is very common for a programmer to make assumptions about what input values can be. You can hear the thoughts, "this method will only be called from this one script, so the input will always be one of these values." Of course, time passes, things change and the next thing you know, your system is dead because some caller didn't use one of those values.

These kinds of assumptions can creep into code in many ways. You can protect against these situations by practicing defensive programming. This includes checking every input and output to make sure the code is being used in a way consistent with its design.

`Xmf\Assert` can be used to perform that checking. Assertions can be made on type or value criteria. Here is an example:

```php
<?php
use Xmf\Assert;
use InvalidArgumentException;

// ...

    try {
        Assert::integer($uid, "Invalid Id");        // must be an integer
        Assert::greaterThan($uid, 0, "Invalid Id"); // must be greater than zero
    } catch(InvalidArgumentException $e) {
        // handle the exception
        redirect_header('index.php', 2, $e->getMessage());
    }

// ...
```

For a complete list of available assertions see the [Assertions Reference](assert.md).

