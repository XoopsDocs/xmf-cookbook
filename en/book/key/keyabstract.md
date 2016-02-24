## KeyAbstract

The `Xmf\Key\KeyAbstract` is an abstract class defines a Key.

The concrete implementations of KeyAbstract are responsible for

* creating keys
* serializing and deserializing key data for storage
* interacting with a StorageInterface implementation for key persistence as needed

### __construct(*$storage*, *$name*)

The StorageInterface instance, *$storage*, handles persistence for this key.
The *$name* parameter is the symbolic name of the key to use.
The *$name* uniquely identifies the key in the key store. The key name should relate to a specific
application action, or a closely related set of actions.

### getSigning()

Returns a key string to be used for signing.

### getVerifying()

Returns a key string to be used for verifying.

### create()

Create the key and store it for use.

Returns true on success, otherwise false.

### kill()

Delete the key from storage.
