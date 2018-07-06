# Admin

## Admin

The `Xmf\Module\Admin` class is a transition wrapper for Module Administration methods. To the extent possible, the next generation \Xoops\Module\Admin methods are supported. Using `Xmf\Module\Admin` instead of the native Frameworks ModuleAdmin in 2.5.x makes the admin area code forward compatible.

### Admin::getInstance\(\)

Retrieve a module admin instance. The return instance may be an instance of `Xmf\Module\Admin`, or a native system class if it is already compatible with `Xmf\Module\Admin`.

### addConfigBoxLine\(_$value_, _$type_\)

Add a line to the config box.

This chart shows the minimal set of acceptable types and value expectation. Additional types may be available, but may produces different results based on the underlying XOOPS version.

| _$type_ | _$value_ |
| --- | --- |
| default | value is message displayed directly \(also used for any unknown types\) |
| folder | value is directory name, will display accept message if it exists, or an error if not |
| chmod | value is array\("directory name", permission\) accept if exists with permission, else error |
| module | value is string module name, or array\(module, type\). If module is installed an accept message displays, otherwise a warning \(if _$value_\[1\]=='warning'\) or an error displays. |

Returns _true_ on success, otherwise _false_.

### addConfigError\(_$value_\)

Add the message _$value_ to the config box as an error

Returns _true_ on success, otherwise _false_.

### addConfigAccept\(_$value_\)

Add the message _$value_ to the config box as an accept \(OK\) message.

Returns _true_ on success, otherwise _false_.

### addConfigWarning\(_$value_\)

Add the message _$value_ to the config box as a warning.

Returns _true_ on success, otherwise _false_.

### addConfigModuleVersion\(_$moddir_, _$minversion_\)

Check for installed module and version and add a config box line, an accept message if module _$moddir_ is installed and is version _$minversion_ or higher, otherwise an error message.

### addInfoBox\(_$title_\)

Add Info box with the specified _$title_.

Returns _true_ on success, otherwise _false_.

### addInfoBoxLine\(_$text_, _$type_, _$color_\)

Add a line with text _$text_ to the info box, with _$type_ and _$color_

Returns _true_ on success, otherwise _false_.

### renderInfoBox\(\)

Return HTML string of rendered InfoBox.

### displayInfoBox\( \)

Display the rendered InfoBox.

### addItemButton\(_$title_, _$link_, _$icon_, _$extra_\)

Add an Item button for displayButtonBox\(\)

Returns _true_ on success, otherwise _false_.

### renderButton\(_$position_, _$delimiter_\)

Return HTML string with all item buttons rendered.

### displayButton\(_$position_, _$delimiter_\)

Display all item buttons

### renderIndex\(\)

Return HTML string of rendered index page for admin

### displayIndex\(\)

Display the rendered index page for admin

### displayNavigation\(_$menu_\)

Display the navigation menu for the page _$menu_

### renderAbout\(_$logo\_xoops_\)

Return HTML string of rendered about page

### displayAbout\(_$logo\_xoops_\)

Display the rendered about page

## Static methods only available in Xmf\Module\Admin

### Admin::iconUrl\(_$name_, _$size_\)

Return an appropriate URL for system provided icons. The icon name is specified in _$name_. If it is blank, only the path will be returned. The size specified in _$size_ should be 16 or 32. The default is 32.

### Admin::menuIconPath\(_$image_\)

Return an appropriate imagePath for the image named _$image_ for use in menu.php.

### Admin::setPaypal\(_$paypal_\)

set paypal for 2.5 renderAbout\(\)/displayAbout\(\).

