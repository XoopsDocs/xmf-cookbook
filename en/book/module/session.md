## Session

The `Xmf\Module\Helper\Session` class is a module aware helper for using the session storage for module related
data. This helper isolates the module related data by applying a module specific prefix to each key.

`Xmf\Module\Helper\Session` extends [Xmf\Module\Helper\AbstractHelper](abstracthelper.php).

### new Session(*$dirname*)

Creates the session helper for the module specified by name as *$dirname*.
If the string *$dirname* is empty, the current module in XOOPS will be used.

### set(*$name*, *$value*)

Sets a the session variable named *$name* to the value *$value*.

### get(*$name*, *$default*)

Returns the session variable named *$name*. If the named variable does not exist, it returns
*$default*, or *false* if *$default* was not specified.

### del($name)

Deletes the session variable named *$name*.

### destroy()

Delete all session variables named by our module.
