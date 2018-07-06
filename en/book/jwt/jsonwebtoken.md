# jsonwebtoken

The `Xmf\Jwt\JsonWebToken` class is used to create and decode JSON Web Tokens. A full description and specification of JSON Web Tokens can be found in [RFC7519](https://tools.ietf.org/html/rfc7519).

## new JsonWebToken\(_$key_, _$algorithm_\)

Instantiates a new JsonWebToken object, using a [Xmf\Key\KeyAbstract](../key/keyabstract.md) object _$key_, using the specified _$algorithm_ for signing and verifying. An invalid algorithm will throw \DomainException.

The default _$algorithm_ is 'HS256', and the currently supplied [TokenFactory](tokenfactory.md) and [TokenReader](tokenreader.md) classes are locked to it. HS256 uses HMAC with SHA256 for signing and verifying.

## setAlgorithm\(_$algorithm_\)

Change the algorithm used for signing/verifying the token. An invalid algorithm will throw \DomainException.

## decode\(_$jwtString_, _$assertClaims_\)

Decode a JWT string _$jwtString_, validating signature and well defined registered claims, and optionally validate against a list of supplied claims in the _$assertClaims_.

Claims such as _'exp'_, expiration time, are automatically enforced. Application specific public or claims to be verified by specifying the required claims in _$assertClaims_ array.

An example array could look like this: `array('aud' => 'myscript');`

If no application claims are to be validated, an empty array \(the default\) should be specified in _$assertClaims_.

Returns the payload of the decoded token as a _stdClass_ object, or false if the token was invalid.

## create\(_$payload_, _$expirationOffset_\)

Create a signed token string for the array of claims specified in _$payload_. The integer _$expirationOffset_ parameter can be used to specify an expiration time as the number of seconds from _now_ that the token will expire. If specified, this will be added as an 'exp' claim to the payload.

Returns a string of the signed token with the specified payload.

