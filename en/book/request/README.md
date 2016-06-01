## Request

The `Xmf\Request` class allows controlled access to HTTP request variables, cleaning the variables
of potentially harmful injections by default, and conforming them to specified types.

### Request::getMethod()
Returns, as a string, the HTTP request method for the current request. Possible values include
'GET', 'HEAD', 'POST', and 'PUT'.

### Request::getVar(*$name*, *$default*, *$hash*, *$type*, *$mask*)
Fetches and returns a named variable from the request data.

This method is invoked by most of the *Request::getXyx()* methods, which accept the same *$name*,
*$default*, and *$hash* parameters. Documentation for those methods will not duplicate the parameter
descriptions presented here.

The name specified in *$name* is the index name in the specified *$hash* that is the source of the
variable to clean.

A default value specified in *$default* will be returned if the named hash index does not exist.

The hash in which the named variable is to be source can be specified in *$hash*.
Recognized hash values are GET, POST, FILES, COOKIE, ENV, and SERVER. These will work on the data normally
contained in the PHP superglobals of the like name. An additional hash value of METHOD will choose the hash
based on the current HTTP request method.

The default, used for any other values, is the data contained in the REQUEST superglobal.

The type specified in *$type* is the data type that controls how the data is cleaned and the type of the
return value. Valid types are described in [FilterInput:clean()](../filterinput/README.php)

A bitmask in *$mask* can specify options to the cleaning process. Possible values are:

| Symbolic Mask Value | Meaning if Set                              |
|---------------------|---------------------------------------------|
| MASK_NO_TRIM        | do not trim leading and trailing whitespace |
| MASK_ALLOW_RAW      | skip cleaning and allow raw input           |
| MASK_ALLOW_HTML     | allow a limited "safe" set of HTML markup   |


### Request::getInt(*$name*, *$default*, *$hash*)

Invokes getVar() requesting an INTEGER type. If not otherwise specified, the default value is 0.
The integer filter will allow only digits to be returned.

Returns an integer.

### Request::getFloat(*$name*, *$default*, *$hash*)
Invokes getVar() requesting an FLOAT type. If not otherwise specified, the default value is 0.0.
The float filter only allows digits and periods.

Returns a float.

### Request::getBool(*$name*, *$default*, *$hash*)
Invokes getVar() requesting an BOOLEAN type. If not otherwise specified, the default value is false.
The bool filter will only return true/false bool values.

Returns a boolean.

### Request::getWord(*$name*, *$default*, *$hash*)
Invokes getVar() requesting an WORD type. If not otherwise specified, the default value is ''.
The word filter only allows the characters [A-Za-z_].

Returns a string.

### Request::getCmd(*$name*, *$default*, *$hash*)
Invokes getVar() requesting an CMD type. If not otherwise specified, the default value is ''.
The cmd filter only allows the characters [A-Za-z0-9.-_] and returns in lower case.

Returns a string.

### Request::getString(*$name*, *$default*, *$hash*, *$mask*)
Invokes getVar() requesting an STRING type. If not otherwise specified, the default value is ''.
The string filter deletes 'bad' HTML code, if not overridden by the mask.

Returns a string.

### Request::getArray(*$name*, *$default*, *$hash*)
Invokes getVar() requesting an ARRAY type. If not otherwise specified, the default value is an empty array.
The array is recursively processed to remove XSS and similar "bad" code.

Returns an array

### Request::getText(*$name*, *$default*, *$hash*)
Fetches and returns raw text by invoking getVar() requesting an STRING type wit a MASK_ALLOW_RAW mask.
If not otherwise specified, the default value is ''.

Returns a string without cleaning.

### Request::getUrl(*$name*, *$default*, *$hash*)
Invokes getVar() requesting an WEBURL type. A WEBURL must be a URL that is relative, or an 'http'
or 'https' scheme. If not otherwise specified, the default value is ''.

Returns a string.

### Request::getPath(*$name*, *$default*, *$hash*)
Invokes getVar() requesting an PATH type. The PATH can be a filesystem or web path.
If not otherwise specified, the default value is ''.

Returns a string, a path or the default.

### Request::getEmail(*$name*, *$default*, *$hash*)
Invokes getVar() requesting an EMAIL type. If not otherwise specified, the default value is ''.

Returns a string, a valid email address or the default.

### Request::getIP(*$name*, *$default*, *$hash*)
Invokes getVar() requesting an IP type. If not otherwise specified, the default value is ''.

Returns a string, a valid IPv4 or IPv6 address, or the default.

### Request::getHeader(*$headerName*, *$default*)
Returns the HTTP request header named *$headerName*, or the default.
If not otherwise specified, the default value is ''.

Returns a string.

### Request::hasVar(*$name*, *$hash*)
Check if the variable named *$name* exists in the hash named *$hash*.

Returns *true* if the named variable exists, otherwise *false*.

### Request::setVar(*$name*, *$value*, *$hash*, *$overwrite*)
Set the variable named *$name* in hash named *$hash*. If the named variable exists,
it will only be overwritten if *$overwrite* is true (which is the default).
A *$hash* value of 'METHOD' (which is the default) will use the hash based on the HTTP request method.

Returns the previous value of the variable or null if not previously set.

### Request::get(*$hash*, *$mask*)
Cleans and returns a copy of an entire hash array.
The hash in *$hash* is treated as described in Request::getVar() with the default of REQUEST.
The bitmask in *$mask* is treated as described in Request::getVar() with a default of 0.

Returns an array.

### Request::set(*$array*, *$hash*, *$overwrite*)

Sets an array of variables, as specified in *$array* as name=>value pairs, in the specified *$hash*.
If the named variable exists, it will only be overwritten if *$overwrite* is true (which is the default).
A *$hash* value of 'METHOD' (which is the default) will use the hash based on the HTTP request method.

This method does not return a value.
