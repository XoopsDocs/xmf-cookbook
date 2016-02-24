## Cache

The `Xmf\Module\Cache` class is a helper for using the system cache for module related data.
The underlying cache is a key value store. This helper wraps the

### new Cache()

public boolean
#write( string $key, mixed $value, integer|null $ttl = null )
Write a value for a key to the cache

public mixed
#read( string $key )
Read value for a key from the cache

public
#delete( string $key )
Delete a key from the cache

public mixed
#cacheRead( string $key, callable $regenFunction, integer|null $ttl = null, mixed $args = null )
cache block wrapper
