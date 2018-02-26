## TokenReader

The `Xmf\Jwt\TokenReader` class provides convenience methods to simplify reading JSON Web Tokens.

### TokenReader::fromString(*$key*, *$token*, *$assertClaims*)
Validate and decode a JSON Web Token string

The *$key* is the key that was used to to sign the token. It may be specified as a
[KeyAbstract](../key/keyabstract.md)  object, or a key name string that will be used
to build a key object using the [KeyFactory](keyfactory.md) using a default [FileStorage](../key/filestorage.md)
instance for storage.

The *$token* is the [JSON Web Token](jsonwebtoken.md) string to decode and validate.

The *$assertClaims* array specifies application specific public or claims that are verified
while decoding.

Returns the token payload as stdClass, or false if token was invalid.

### TokenReader::fromCookie(*$key*, *$cookieName*, *$assertClaims*)

Extracts a token string from the cookie named by *$cookieName*, and uses `TokenReader::fromString()`
to process using the specified *$key* and *$assertClaims*.

Returns the token payload as stdClass, or false if token was invalid.

### TokenReader::fromRequest(*$key*, *$attributeName*,  *$assertClaims*)

Extracts a token string from the cookie named by *$attributeName*, and uses `TokenReader::fromString()`
to process using the specified *$key* and *$assertClaims*.

Returns the token payload as stdClass, or false if token was invalid.

### TokenReader::fromHeader(*$key*, *$assertClaims*, *$headerName*)
Extracts a token string from the cookie named by *$headerName*, and uses `TokenReader::fromString()`
to process using the specified *$key* and *$assertClaims*.

The header is expected to be an bearer token in the authorization header. The default
for *$headerName* should not normally need to be changed.


Returns the token payload as stdClass, or false if token was invalid.
