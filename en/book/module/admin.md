## Admin

The `Xmf\Module\Admin` class is a transition wrapper for Module Administration methods. To the extent
possible, the next generation \Xoops\Module\Admin methods are supported. Using `Xmf\Module\Admin` instead
of the native Frameworks ModuleAdmin in 2.5.x makes the admin area code forward compatible.

### Admin::getInstance()

Retrieve a module admin instance. The return instance may be an instance of `Xmf\Module\Admin`,
or a native system class if it is already compatible with `Xmf\Module\Admin`.

### addConfigBoxLine(*$value*, *$type*)

Add line to the config box.

This chart shows the minimal set of acceptable types and value expectation.
Additional types may be available, but may produces different results based on the underlying XOOPS version.

| *$type* | *$value* |
|---------|----------|
| default | value is message displayed directly (also used for any unknown types)|
| folder  | value is directory name, will display accept message if it exists, or an error if not |
| chmod   | value is array("directory name", permission) accept if exists with permission, else error |
| module  | value is string module name, or array(module, type). If module is installed an accept message displays, otherwise a warning (if *$value*[1]=='warning') or an error displays. |

Returns *true* on success, otherwise *false*.

### addInfoBox(*$title*)
Add Info box with the specified *$title*.

Returns *true* on success, otherwise *false*.

### addInfoBoxLine(*$text*, *$type*, *$color*)

Add line with text *$text* to the info box, with *$type* and *$color*

Returns *true* on success, otherwise *false*.

### addItemButton(*$title*, *$link*, *$icon*, *$extra*)

Add Item button for displayButtonBox()

Returns *true* on success, otherwise *false*.

### renderButton(*$position*, *$delimiter*)

Return HTML string with all item buttons rendered.

### displayButton(*$position*, *$delimiter*)

Display all item buttons

### renderInfoBox()

Return HTML string of rendered InfoBox.

### displayInfoBox( )

Display the rendered InfoBox.

### renderIndex()

Return HTML string of rendered index page for admin

### displayIndex()

Display the rendered index page for admin


### displayNavigation( string $menu = '' )
Display the navigation menu

### renderAbout(*$logo_xoops*)

Return HTML string of rendered about page

### displayAbout(*$logo_xoops*)
Display the rendered about  page

### addConfigError(*$value*)

Add the message *$value* to the config box as an error

Returns *true* on success, otherwise *false*.

### addConfigAccept(*$value*)

Add the message *$value* to the config box as an accept (OK) message.

Returns *true* on success, otherwise *false*.

### addConfigWarning(*$value*)

Add the message *$value* to the config box as a warning.

Returns *true* on success, otherwise *false*.

### addConfigModuleVersion(*$moddir*, *$minversion*)
Check for installed module and version and add a config box line, an accept message if module *$moddir* is
installed and is version *$minversion* or higher, otherwise an error message.

## Static methods only available in Xmf\Module\Admin

### Admin::iconUrl(*$name*, *$size*)
Return an appropriate URL for system provided icons. The icon name is specified in *$name*. If it is blank,
only the path will be returned. The size specified in *$size* should be 16 or 32. The default is 32.

### Admin::menuIconPath(*$image*)
Return an appropriate imagePath for the image named *$image* for use in menu.php.

### Admin::setPaypal(*$paypal*)
set paypal for 2.5 renderAbout()/displayAbout().

