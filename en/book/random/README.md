## Random

The `Xmf\Random` class produces random strings for use as tokens or keys. While these methods
have controlling parameters, the default values were carefully researched and selected. If you
need the control, please refer to the source code, and the documentation of the supporting
[RandomLib library](https://github.com/ircmaxell/RandomLib).

### generateOneTimeToken()

Return a hashed random number suitable for use as a one time token.

### generateKey()

Return a hashed random number suitable for use as a medium strength key.
