# StorageInterface

The `Xmf\Key\StorageInterface` interface defines the methods used to store and retrieve keys.

The key data is treated as string data. The actual Key class is responsible for any serialization or deserialization needed.

The _$name_ parameter common to all methods is a string key name, the symbolic name of the key to use. The _$name_ uniquely identifies the key in the key store. The key name should relate to a specific application action, or a closely related set of actions.

## save\(_$name_, _$data_\)

Save key data _$data_ under the name _$name_.

Returns true if successful, otherwise false.

## fetch\(_$name_\)

Fetch key data stored under the name _$name_.

Returns the stored key data if successful, otherwise false.

## exists\(_$name_\)

Check for the existence of a key under the name _$name_.

Returns true if a key named _$name_ exists, otherwise false.

## delete\(_$name_\)

Delete a any key stored under the name _$name_.

Returns true if successful, otherwise false.

