# TokenFactory

The `Xmf\Jwt\TokenFactory` class provides a convenient factory method to simplify creating JSON Web Token strings.

## TokenFactory::build\(_$key_, _$payload_, _$expirationOffset_\)

This method creates and returns a JSON Web Token string.

The _$key_ is used to to sign the token. It may be specified as a [KeyAbstract](../key/keyabstract.md) object, or a key name string that will be used to build a key object using the [KeyFactory](keyfactory.md) using a default [FileStorage](../key/filestorage.md) instance for storage.

The _$payload_ is an associative array of claims included in the token, elements in the form claim =&gt; value.

The _$expirationOffset_ is an integer that specifies an expiration time as the number of seconds from _now_ that the token will expire. If specified, this will be added as an 'exp' claim to the payload.

If the token cannot be generated, an exception will be thrown. Possible exceptions include:

* DomainException;
* InvalidArgumentException;
* UnexpectedValueException;

