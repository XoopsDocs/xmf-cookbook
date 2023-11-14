# Helper

The `Xmf\Module\Helper` class is used to obtain a module helper. A module helper can simplify routine module related operations.

For XOOPS 2.5 systems, the module helper returned will be an instance of the [Xmf\Module\Helper\GenericHelper](helper-1/generichelper.md).

## getHelper\(_$dirname_\)

Get an instance to a module helper for a module directory in _$dirname_.

Returns a Helper instance or false on error.

## getModule\(\)

Returns a XoopsModule object for the module represented by this Helper.

## getConfig\(_$name_, _$default_\)

Returns the value of the module config item _$name_, or an array of all config items if _$name_ is empty or not specified. If config item _$name_ does not exist _$default_, null if not specified, is returned.

## getHandler\(_$name_\)

Returns an Object Handler for the module's _$name_ handler, or false if the handler does not exist.

## loadLanguage\(_$name_\)

Load language support for _$name_ for this module

## setDebug\(_$bool_\)

Set debug option for the helper on \(_true_\) or off \(_false_.\) The default for _$bool_, if not specified, is _true_.

## addLog\(_$log_\)

Add the message string _$log_ to the module log.

## isCurrentModule\(\)

Returns true if this module is the currently active module, otherwise false.

## isUserAdmin\(\)

Returns true if the current user has admin rights to this module, otherwise false.

## url\(_$url_\)

Returns an absolute URL for a module relative URL specified in _$url_.

## path\( string $path = '' \)

Returns an absolute filesystem path for a module relative path specified in _$path_.

## redirect\(_$url_, _$time_, _$message_\)

Redirects the session within the same module, to the module relative URL specified in _$url_.

## uploadUrl\(_$url_\)

Return absolute URL for a module relative upload file specified in _$url_.

## uploadPath\( string $path = '' \)

Return absolute filesystem path for a module relative upload file specified in _$path_.
