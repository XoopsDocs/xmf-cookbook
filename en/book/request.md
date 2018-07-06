# README

The `Xmf\Request` class allows controlled access to HTTP request variables, cleaning the variables of potentially harmful injections by default, and conforming them to specified types.

## Request::getMethod\(\)

Returns, as a string, the HTTP request method for the current request. Possible values include 'GET', 'HEAD', 'POST', and 'PUT'.

## Request::getVar\(_$name_, _$default_, _$hash_, _$type_, _$mask_\)

Fetches and returns a named variable from the request data.

This method is invoked by most of the _Request::getXyx\(\)_ methods, which accept the same _$name_, _$default_, and _$hash_ parameters. Documentation for those methods will not duplicate the parameter descriptions presented here.

The name specified in _$name_ is the index name in the specified _$hash_ that is the source of the variable to clean.

A default value specified in _$default_ will be returned if the named hash index does not exist.

The hash in which the named variable is to be source can be specified in _$hash_. Recognized hash values are GET, POST, FILES, COOKIE, ENV, and SERVER. These will work on the data normally contained in the PHP superglobals of the like name. An additional hash value of METHOD will choose the hash based on the current HTTP request method.

The default, used for any other values, is the data contained in the REQUEST superglobal.

The type specified in _$type_ is the data type that controls how the data is cleaned and the type of the return value. Valid types are described in [FilterInput:clean\(\)](https://github.com/xoops/xmf-cookbook/tree/2971b4bb568db7c6791e293e50ffc917d75ed81f/en/book/filterinput/README.php)

A bitmask in _$mask_ can specify options to the cleaning process. Possible values are:

| Symbolic Mask Value | Meaning if Set |
| --- | --- |
| MASK\_NO\_TRIM | do not trim leading and trailing whitespace |
| MASK\_ALLOW\_RAW | skip cleaning and allow raw input |
| MASK\_ALLOW\_HTML | allow a limited "safe" set of HTML markup |

## Request::getInt\(_$name_, _$default_, _$hash_\)

Invokes getVar\(\) requesting an INTEGER type. If not otherwise specified, the default value is 0. The integer filter will allow only digits to be returned.

Returns an integer.

## Request::getFloat\(_$name_, _$default_, _$hash_\)

Invokes getVar\(\) requesting an FLOAT type. If not otherwise specified, the default value is 0.0. The float filter only allows digits and periods.

Returns a float.

## Request::getBool\(_$name_, _$default_, _$hash_\)

Invokes getVar\(\) requesting an BOOLEAN type. If not otherwise specified, the default value is false. The bool filter will only return true/false bool values.

Returns a boolean.

## Request::getWord\(_$name_, _$default_, _$hash_\)

Invokes getVar\(\) requesting an WORD type. If not otherwise specified, the default value is ''. The word filter only allows the characters \[A-Za-z\_\].

Returns a string.

## Request::getCmd\(_$name_, _$default_, _$hash_\)

Invokes getVar\(\) requesting an CMD type. If not otherwise specified, the default value is ''. The cmd filter only allows the characters \[A-Za-z0-9.-\_\] and returns in lower case.

Returns a string.

## Request::getString\(_$name_, _$default_, _$hash_, _$mask_\)

Invokes getVar\(\) requesting an STRING type. If not otherwise specified, the default value is ''. The string filter deletes 'bad' HTML code, if not overridden by the mask.

Returns a string.

## Request::getArray\(_$name_, _$default_, _$hash_\)

Invokes getVar\(\) requesting an ARRAY type. If not otherwise specified, the default value is an empty array. The array is recursively processed to remove XSS and similar "bad" code.

Returns an array

## Request::getText\(_$name_, _$default_, _$hash_\)

Fetches and returns raw text by invoking getVar\(\) requesting an STRING type wit a MASK\_ALLOW\_RAW mask. If not otherwise specified, the default value is ''.

Returns a string without cleaning.

## Request::getUrl\(_$name_, _$default_, _$hash_\)

Invokes getVar\(\) requesting an WEBURL type. A WEBURL must be a URL that is relative, or an 'http' or 'https' scheme. If not otherwise specified, the default value is ''.

Returns a string.

## Request::getPath\(_$name_, _$default_, _$hash_\)

Invokes getVar\(\) requesting an PATH type. The PATH can be a filesystem or web path. If not otherwise specified, the default value is ''.

Returns a string, a path or the default.

## Request::getEmail\(_$name_, _$default_, _$hash_\)

Invokes getVar\(\) requesting an EMAIL type. If not otherwise specified, the default value is ''.

Returns a string, a valid email address or the default.

## Request::getIP\(_$name_, _$default_, _$hash_\)

Invokes getVar\(\) requesting an IP type. If not otherwise specified, the default value is ''.

Returns a string, a valid IPv4 or IPv6 address, or the default.

## Request::getHeader\(_$headerName_, _$default_\)

Returns the HTTP request header named _$headerName_, or the default. If not otherwise specified, the default value is ''.

Returns a string.

## Request::hasVar\(_$name_, _$hash_\)

Check if the variable named _$name_ exists in the hash named _$hash_.

Returns _true_ if the named variable exists, otherwise _false_.

## Request::setVar\(_$name_, _$value_, _$hash_, _$overwrite_\)

Set the variable named _$name_ in hash named _$hash_. If the named variable exists, it will only be overwritten if _$overwrite_ is true \(which is the default\). A _$hash_ value of 'METHOD' \(which is the default\) will use the hash based on the HTTP request method.

Returns the previous value of the variable or null if not previously set.

## Request::get\(_$hash_, _$mask_\)

Cleans and returns a copy of an entire hash array. The hash in _$hash_ is treated as described in Request::getVar\(\) with the default of REQUEST. The bitmask in _$mask_ is treated as described in Request::getVar\(\) with a default of 0.

Returns an array.

## Request::set\(_$array_, _$hash_, _$overwrite_\)

Sets an array of variables, as specified in _$array_ as name=&gt;value pairs, in the specified _$hash_. If the named variable exists, it will only be overwritten if _$overwrite_ is true \(which is the default\). A _$hash_ value of 'METHOD' \(which is the default\) will use the hash based on the HTTP request method.

This method does not return a value.

