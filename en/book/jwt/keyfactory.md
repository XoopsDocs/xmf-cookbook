## KeyFactory

The `Xmf\Jwt\KeyFactory` class is a factory used to build key objects for use in
a [JsonWebToken](jsonwebtoken.md) object.

### :KeyFactory:build(*$keyName*)

Returns a `Xmf\Key\Basic` key object for JWT use based on default choices. If the key, specified by name
in *$keyName*, has not been established, it will be created.

The *$keyName* key name is a string, the sysmbolic name of the key to use. The *$keyName* uniquely
identifies a key in a key store, as defined by the interface `Xmf\Key\StorageInterface`.
The key name should relate to a specific application action, or a closely related set of actions.
