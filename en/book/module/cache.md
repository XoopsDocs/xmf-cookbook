# Cache

The `Xmf\Module\Helper\Cache` class is a module aware helper for using the system cache for module related data. The underlying cache is a key value store. This helper isolates the module related data by applying a module specific prefix to each key.

`Xmf\Module\Helper\Cache` extends [Xmf\Module\Helper\AbstractHelper](https://github.com/XoopsDocs/xmf-cookbook/tree/fe9f7aa71cb38a3faba2ff745352b2de77a33b6f/en/book/module/abstracthelper.php).

## new Cache\(_$dirname_\)

Creates the cache helper for the module specified by name as _$dirname_. If the string _$dirname_ is empty, the current module in XOOPS will be used.

## write\(_$key_, _$value_, _$ttl_\)

Write the value _$value_ for a key named _$key_ to the cache, using the specified number of seconds in _$ttl_ as the time to live.

## read\(_$key_, _$default_\)

Read value for the key named _$key_ from the cache. If the key does not exist, it returns _$default_, or _false_ if _$default_ was not specified.

## delete\(_$key_\)

Deletes any key named _$key_ from the cache.

## cacheRead\(_$key_, _$regenFunction_, _$ttl_, _$args_\)

The cacheRead\(\) method combines reading and any needed regenerating of the cache entry into a single call.

First, it attempts to read the cache entry for _$key_, and returns it if found.

If the cache read fails, it calls the specified callable, _$regenFunction_, passing to it any variable arguments, _$args_. It writes the return of _$regenFunction_ to the cache for _$key_ with time to live _$ttl_, and returns the new cached value to the caller.

