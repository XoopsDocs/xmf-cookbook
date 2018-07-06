# KeyAbstract

The `Xmf\Key\KeyAbstract` is an abstract class that defines a Key.

The concrete implementations of KeyAbstract are responsible for

* creating keys
* serializing and deserializing key data for storage
* interacting with a StorageInterface implementation for key persistence as needed

## \_\_construct\(_$storage_, _$name_\)

The StorageInterface instance, _$storage_, handles persistence for this key. The _$name_ parameter is the symbolic name of the key to use. The _$name_ uniquely identifies the key in the key store. The key name should relate to a specific application action, or a closely related set of actions.

## getSigning\(\)

Returns a key string to be used for signing.

## getVerifying\(\)

Returns a key string to be used for verifying.

## create\(\)

Create the key and store it for use.

Returns true on success, otherwise false.

## kill\(\)

Delete the key from storage.

