# session

The `Xmf\Module\Helper\Session` class is a module aware helper for using the session storage for module related data. This helper isolates the module related data by applying a module specific prefix to each key.

`Xmf\Module\Helper\Session` extends [Xmf\Module\Helper\AbstractHelper](https://github.com/xoops/xmf-cookbook/tree/2971b4bb568db7c6791e293e50ffc917d75ed81f/en/book/module/abstracthelper.php).

## new Session\(_$dirname_\)

Creates the session helper for the module specified by name as _$dirname_. If the string _$dirname_ is empty, the current module in XOOPS will be used.

## set\(_$name_, _$value_\)

Sets a the session variable named _$name_ to the value _$value_.

## get\(_$name_, _$default_\)

Returns the session variable named _$name_. If the named variable does not exist, it returns _$default_, or _false_ if _$default_ was not specified.

## del\($name\)

Deletes the session variable named _$name_.

## destroy\(\)

Delete all session variables named by our module.

