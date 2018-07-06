# basic

The `Xmf\Key\Basic` class is a [Xmf\Key\KeyAbstract](keyabstract.md) implementation that provides a key suitable for HMAC signing.

## new Basic\(_$storage_, _$name_\)

The StorageInterface instance, _$storage_, handles persistence for this key. The _$name_ parameter is the symbolic name of the key to use.

## getSigning\(\)

Returns a key string to be used for signing.

## getVerifying\(\)

Returns a key string to be used for verifying.

## create\(\)

Create the key and store it for use.

Returns true on success, otherwise false.

## kill\(\)

Delete the key from storage.

