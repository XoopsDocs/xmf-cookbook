## Basic

The `Xmf\Key\Basic` class is a [Xmf\Key\KeyAbstract](keyabstract.md) implementation that provides
a key suitable for HMAC signing.

### new Basic(*$storage*, *$name*)

The StorageInterface instance, *$storage*, handles persistence for this key.
The *$name* parameter is the symbolic name of the key to use.

### getSigning()

Returns a key string to be used for signing.

### getVerifying()

Returns a key string to be used for verifying.

### create()

Create the key and store it for use.

Returns true on success, otherwise false.

### kill()

Delete the key from storage.
