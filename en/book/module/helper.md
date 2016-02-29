## Helper

The `Xmf\Module\Helper` class is used to obtain a module helper. A module helper can simplify
routine module related operations.

For XOOPS 2.5 systems, the module helper returned will be an instance of the
[Xmf\Module\Helper\GenericHelper](generichelper.md).

### getHelper(*$dirname*)

Get an instance to a module helper for a module directory in *$dirname*.

Returns a Helper instance or false on error.

### getModule()

Returns a XoopsModule object for the module represented by this Helper.

### getConfig(*$name*, *$default*)

Returns the value of the module config item *$name*, or an array of all config items
if *$name* is empty or not specified. If config item *$name* does not exist *$default*,
null if not specified, is returned.

### getHandler(*$name*)

Returns an Object Handler for the module's *$name* handler, or false if the handler does not exist.

### loadLanguage(*$name*)

Load language support for *$name* for this module

### setDebug(*$bool*)

Set debug option for the helper on (*true*) or off (*false*.)
The default for *$bool*, if not specified, is *true*.

### addLog(*$log*)

Add the message string *$log* to the module log.

### isCurrentModule()

Returns true if this module is the currently active module, otherwise false.

### isUserAdmin()

Returns true if the current user has admin rights to this module, otherwise false.

### url(*$url*)

Returns an absolute URL for a module relative URL specified in *$url*.

### path( string $path = '' )

Returns an absolute filesystem path for a module relative path specified in *$path*.

### redirect(*$url*, *$time*, *$message*)

Redirects the session within the same module, to the module relative URL specified in *$url*.
