# Using the Session Helper

Saving context information is a common need. Often times programmers jump straight to the HTTP cookie to save context between browser requests. Often times, this is overkill. XOOPS maintains a very capable session mechanism. If your data only needs to last until the user logs out, using the session instead of a cookie may be more efficient. So if you need to remember something like the last set of criteria a user entered on a certain page of your site, consider the session before the cookie.

The [Xmf\Module\Helper\Session](../reference/module/helper-1/session.md) class does a number of favors for you. First, it is module aware. It will use your current module name as a prefix to your session key. Using this approach, we can share the session space between the core system and other modules without having conflicts in our names. Also, your value is always serialized before it is saved in the session, so you can store anything without worrying about the type, or converting it back and forth. \(If you do store an object, make sure the class for that object is available before you `get()` it.\)

Here is how you can save data to the session using XMF. For this example, we assume your data is in the variable $value, and your key is 'context'. Value can be pretty much anything, a single value, an array, even an object.

## Save and Retrieve Context

The fist step is always to get a session helper.

```php
$sessionHelper = new \Xmf\Module\Helper\Session();
```

Save the data like this:

```php
$sessionHelper->set('context', $value);
```

Retrieving your value is just as easy:

```php
$value = $sessionHelper->get('context');
```

If you are finished with the value you saved and no longer need it, you can delete it:

```php
$sessionHelper->del('context');
```

All session data will disappear once the user logs out, or the session expires from inactivity.

