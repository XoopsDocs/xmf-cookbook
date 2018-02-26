## Cache

The `Xmf\Module\Helper\Cache` class is a module aware helper for using the system cache for module
related data. The underlying cache is a key value store. This helper isolates the module related data
by applying a module specific prefix to each key.

`Xmf\Module\Helper\Cache` extends [Xmf\Module\Helper\AbstractHelper](abstracthelper.php).

### new Cache(*$dirname*)

Creates the cache helper for the module specified by name as *$dirname*.
If the string *$dirname* is empty, the current module in XOOPS will be used.

### write(*$key*, *$value*, *$ttl*)

Write the value *$value* for a key named *$key* to the cache, using the specified number of seconds in *$ttl*
as the time to live.

### read(*$key*, *$default*)

Read value for the key named *$key* from the cache. If the key does not exist, it returns
*$default*, or *false* if *$default* was not specified.

### delete(*$key*)

Deletes any key named *$key* from the cache.

### cacheRead(*$key*, *$regenFunction*, *$ttl*, *$args*)

The cacheRead() method combines reading and any needed regenerating of the cache entry into a single call.

First, it attempts to read the cache entry for *$key*, and returns it if found.

If the cache read fails, it calls the specified callable, *$regenFunction*, passing to it any
variable arguments,  *$args*. It writes the return of *$regenFunction* to the cache for *$key*
with time to live *$ttl*, and returns the new cached value to the caller.
