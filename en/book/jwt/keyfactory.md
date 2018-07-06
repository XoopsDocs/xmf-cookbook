# KeyFactory

The `Xmf\Jwt\KeyFactory` class is a factory used to build key objects for use in a [JsonWebToken](jsonwebtoken.md) object.

## KeyFactory:build\(_$keyName_, _$storage_ = null\)

Returns a `Xmf\Key\Basic` key object for JWT use based on default choices. If the key, specified by name in _$keyName_, has not been established, it will be created.

The _$keyName_ key name is a string, the symbolic name of the key to use. The _$keyName_ uniquely identifies a key in a key store, as defined by the interface `Xmf\Key\StorageInterface`. The key name should relate to a specific application action, or a closely related set of actions.

If specified, _$storage_ should be an instance of `Xmf\Key\StorageInterface`. If _null_ a default [FileStorage](../key/filestorage.md) instance will be used.

