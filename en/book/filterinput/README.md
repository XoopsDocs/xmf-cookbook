## FilterInput

The `Xmf\FilterInput` class support cleaning and filtering data

### FilterInput::getInstance()
Returns a `Xmf\FilterInput` object, only creating it if it does not already exist.

It is possible to customize the behavior of FilterInput by passing configuration variables to getInstance().
See the source for more information.

### process(*$source*)

Clean the *$source*, a string or array of values, processing to remove XSS and other *bad* code.

Returns the *cleaned* version of *$source*.

### FilterInput::clean(*$source*, *$type*)

Cleans the input *$source* removing XSS and other *bad* code using the defaults.
Also, filters the input, conforming to the specified *$type*. 'STRING' is the default *$type*.

Available type are the same as documented with the cleanVar() method.

### cleanVar(*$source*, *$type*)

Cleans the input *$source* with rules established when the instance of FilterInput
was instantiated. Also, filters the input, conforming it to the specified *$type*.
'STRING' is the default *$type*.

Available type are:

| Type | Allowed value |
|------|---------------|
| ALPHANUM or ALNUM | Alphanumeric |
| ARRAY | Recursively cleans each element |
| BASE64 | Base64 encoded |
| BOOLEAN or BOOL | true or false |
| CMD | Command - only characters A-Z, 0-9, underscore, dash and period, forced to lower case. |
| EMAIL | a valid email address |
| FLOAT or DOUBLE | floating point number |
| INTEGER or INT | an integer |
| IP | a valid IP address |
| PATH | a filesystem or web path |
| STRING | a string |
| USERNAME | Username |
| WEBURL | a web URL |
| WORD | only letters A-Z and underscore |

Returns the *cleaned* version of *$source*.
