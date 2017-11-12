## Random

The `Xmf\Random` class produces random strings for use as tokens or keys.

All methods may throw an `\Exception` if a suitable random number cannot be
generated. See the [random_bytes()](http://php.net/manual/en/function.random-bytes.php) documentation for more information.

### generateOneTimeToken()

Return a hashed random number suitable for use as a one time token.

### generateKey()

Return a hashed random number suitable for use as a medium strength key.
