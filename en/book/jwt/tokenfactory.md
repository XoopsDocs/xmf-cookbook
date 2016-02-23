## TokenFactory

The `Xmf\Jwt\TokenFactory` class provides a convenient factory method to simplify creating
JSON Web Token strings.

### TokenFactory::build(*$keyName*, *$payload*, *$expirationOffset*)

This method creates and returns a JSON Web Token string.

The *$keyName* is used to create a key using the [KeyFactory](keyfactory.md), that is used to sign the token.

The *$payload* is an associative array of claims included in the token, elements in the form claim => value.

The *$expirationOffset* is an integer that specifies an expiration time as the number of
seconds from *now* that the token will expire. If specified, this will be added as an 'exp' claim to
the payload.

If the token cannot be generated, an exception will be thrown. Possible exceptions include:

 - DomainException;
 - InvalidArgumentException;
 - UnexpectedValueException;
