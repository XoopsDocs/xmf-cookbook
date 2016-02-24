## Namespaces

XMF uses PHP namespaces. These are new to XOOPS, so take a few minutes to learn about them.
You can read the PHP manual here:

http://php.net/manual/en/language.namespaces.php

### Global Space
Without namespaces, all entities defined in a PHP program end up in a global space. For example,
the PHP built in class `ArrayObject` is in the global space.

This name is pretty well known to PHP programmers, and is documented in the PHP manual, but let's
imagine that we didn't know about it, and wrote our new cool class like this:

```
<?php

class ArrayObject {
    public function doStuff() {
        // ...
    }
}
```

When we try and run it, we get this:

> PHP Fatal error:  Cannot redeclare class ArrayObject ...

Now consider for the code you write, how many things are sharing the global space you depend on.
For a small, self contained system, that might not be a huge issue. But, for larger complex systems,
especially those which incorporate optional code additions from many sources, problems become inevitable.

Now consider that larger complex system we just talked about could describe a XOOPS installation.

What to do?

### Namespaces to the Rescue

PHP has a feature call namespaces. A namespace is a name, or set of nested names, that creates a set
of symbols and names that are not global. Let's make a small change to our example, to illustrate
this.

```
<?php
namespace MyNamespace;

class ArrayObject {
    public function doStuff() {
        // ...
    }
}
```

PHP is happy now.

If all of our code is in the same namespace, we can use our class like this:

```
<?php
namespace MyNamespace;

    // ...
    $object = new ArrayObject();
    // ...
```

But, if everything that uses your class also has to be in your namespace, that gets us right back to the
same problems with sharing a namespace.

That new class we created is actually `\MyNamespace\ArrayObject`. To instantiate it we can do this, anywhere:

```
    $object = new \MyNamespace\ArrayObject();
```

or, if we prefer, we can tell PHP to use a namespace when it sees our class name.

```
<?php
use MyNamespace\ArrayObject;

    // ...
    $object = new ArrayObject();
    // ...
```

When the code in the script refers to `ArrayObject`, it will **use** our MyNamespace version.
The *use* statement can simplify the long namespace declarations, making them easier to work with.
It can even change a name if needed. Be sure and
[read the manual](http://php.net/manual/en/language.namespaces.importing.php) for details.

This brings up an issue. How could we use the real PHP ArrayObject if needed? The answer is to add a
leading backslash. That leading backslash tells PHP start looking from the highest global namespace.

```
<?php
use MyNamespace\ArrayObject;

    // ...
    $object1 = new ArrayObject();

    $object2 = new \ArrayObject();
    // ...
```

Now, `$object1` is an instance of our object, while `$object2` is an instance of the PHP supplied object.

Yes, that can get confusing. So PHP best practice suggestions discourages creating this sort of
ambiguous situation, especially with the built-in class names.

### Xmf Namepace

All Xmf classes are in the `Xmf` namespace. Some classes are levels of namespaces. For example,
the [module](../module/README.md) related classes are in the `Xmf\Module` namespace.

Throughout this document we will always mention the full namespace of the Xmf classes as we refer to them.

### In Closing

Namespaces become increasingly important as PHP development processes and standards mature, and are
a major benefit to sharing open source code between projects. XMF introduces these to XOOPS, and future
XOOPS versions will be built with them.

Once you understand PHP namespaces, you'll find they are a very powerful tool that can make your
programming experience easier when *you* can manage the names, instead of the names managing you.
