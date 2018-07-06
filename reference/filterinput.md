# FilterInput

The `Xmf\FilterInput` class support cleaning and filtering data

## FilterInput::getInstance\(\)

Returns a `Xmf\FilterInput` object, only creating it if it does not already exist.

It is possible to customize the behavior of FilterInput by passing configuration variables to getInstance\(\). See the source for more information.

## process\(_$source_\)

Clean the _$source_, a string or array of values, processing to remove XSS and other _bad_ code.

Returns the _cleaned_ version of _$source_.

## FilterInput::clean\(_$source_, _$type_\)

Cleans the input _$source_ removing XSS and other _bad_ code using the defaults. Also, filters the input, conforming to the specified _$type_. 'STRING' is the default _$type_.

Available type are the same as documented with the cleanVar\(\) method.

## cleanVar\(_$source_, _$type_\)

Cleans the input _$source_ with rules established when the instance of FilterInput was instantiated. Also, filters the input, conforming it to the specified _$type_. 'STRING' is the default _$type_.

Available type are:

| Type | Allowed value |
| --- | --- |
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

Returns the _cleaned_ version of _$source_.

