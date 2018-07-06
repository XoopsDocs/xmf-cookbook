# TokenReader

The `Xmf\Jwt\TokenReader` class provides convenience methods to simplify reading JSON Web Tokens.

## TokenReader::fromString\(_$key_, _$token_, _$assertClaims_\)

Validate and decode a JSON Web Token string

The _$key_ is the key that was used to to sign the token. It may be specified as a [KeyAbstract](../key/keyabstract.md) object, or a key name string that will be used to build a key object using the [KeyFactory](keyfactory.md) using a default [FileStorage](../key/filestorage.md) instance for storage.

The _$token_ is the [JSON Web Token](jsonwebtoken.md) string to decode and validate.

The _$assertClaims_ array specifies application specific public or claims that are verified while decoding.

Returns the token payload as stdClass, or false if token was invalid.

## TokenReader::fromCookie\(_$key_, _$cookieName_, _$assertClaims_\)

Extracts a token string from the cookie named by _$cookieName_, and uses `TokenReader::fromString()` to process using the specified _$key_ and _$assertClaims_.

Returns the token payload as stdClass, or false if token was invalid.

## TokenReader::fromRequest\(_$key_, _$attributeName_,  _$assertClaims_\)

Extracts a token string from the cookie named by _$attributeName_, and uses `TokenReader::fromString()` to process using the specified _$key_ and _$assertClaims_.

Returns the token payload as stdClass, or false if token was invalid.

## TokenReader::fromHeader\(_$key_, _$assertClaims_, _$headerName_\)

Extracts a token string from the cookie named by _$headerName_, and uses `TokenReader::fromString()` to process using the specified _$key_ and _$assertClaims_.

The header is expected to be an bearer token in the authorization header. The default for _$headerName_ should not normally need to be changed.

Returns the token payload as stdClass, or false if token was invalid.

