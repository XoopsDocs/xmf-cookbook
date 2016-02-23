## JsonWebToken

The `Xmf\Jwt\JsonWebToken` class is used to create and decode JSON Web Tokens.

### new JsonWebToken(*$key*, *$algorithm*)
Instantiates a new JsonWebToken object, using a \Xmf\Key\KeyAbstract object *$key*, using the specified
*$algorithm* for signing and verifying. An invalid algorithm will throw \DomainException.

The default *$algorithm* is 'HS256', and the currently supplied [TokenFactory](tokenfactory.md)
and [TokenReader](tokenreader.md) classes are locked to it.
HS256 uses HMAC with SHA256 for signing and verifying.

### setAlgorithm(*$algorithm*)

Change the algorithm used for signing/verifying the token. An invalid algorithm will throw \DomainException.


### decode(*$jwtString*, *$assertClaims*)

Decode a JWT string *$jwtString*, validating signature and well defined registered claims, and optionally
validate against a list of supplied claims in the *$assertClaims*.

Claims such as *'exp'*, expiration time, are automatically enforced. Application specific public or claims
to be verified by specifying the required claims in *$assertClaims* array.

An example array could look like this: `array('aud' => 'myscript');`

If no application claims are to be validated, an empty array (the default) should be specified
in *$assertClaims*.

Returns the payload of the decoded token as a *stdClass* object, or false if the token was invalid.

### create(*$payload*, *$expirationOffset*)

Create a signed token string for the array of claims specified in *$payload*.
The integer *$expirationOffset* parameter can be used to specify an expiration time as the number of
seconds from *now* that the token will expire. If specified, this will be added as an 'exp' claim to
the payload.

Returns a string of the signed token with the specified payload.
