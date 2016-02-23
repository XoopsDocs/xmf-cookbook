## TokenReader

The `Xmf\Jwt\TokenReader` class provides convenience methods to simplify reading JSON Web Tokens.

### TokenReader::fromString(*$keyName*, *$token*, *$assertClaims*)
Validate and decode a JSON Web Token string

The *$keyName* is used to create a key using the [KeyFactory](keyfactory.md), that is used to sign the token.

The *$token* is the [JSON Web Token](jsonwebtoken.md) string to decode and validate.

The *$assertClaims* array specifies application specific public or claims that are verified
while decoding.

Returns the token payload as stdClass, or false if token was invalid.

### TokenReader::fromCookie(*$keyName*, *$cookieName*, *$assertClaims*)

Extracts a token string from the cookie named by *$cookieName*, and uses `TokenReader::fromString()`
to process using the specifed *$keyName* and *$assertClaims*.

Returns the token payload as stdClass, or false if token was invalid.

### TokenReader::fromRequest(*$keyName*, *$attributeName*,  *$assertClaims*)

Extracts a token string from the cookie named by *$attributeName*, and uses `TokenReader::fromString()`
to process using the specifed *$keyName* and *$assertClaims*.

Returns the token payload as stdClass, or false if token was invalid.

### TokenReader::fromHeader(*$keyName*, *$assertClaims*, *$headerName*)
Extracts a token string from the cookie named by *$headerName*, and uses `TokenReader::fromString()`
to process using the specifed *$keyName* and *$assertClaims*.

The header is expected to be an bearer *$headerName*token in the authorization header. The default
for *$headerName* should not normally need to be changed.


Returns the token payload as stdClass, or false if token was invalid.
