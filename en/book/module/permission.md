## Permission

The `Xmf\Module\Helper\Permission` class is a module aware helper for simplified access to system group
permissions in a module.

System group permissions use a string *$gperm_name* as a permission name, and an
integer *$gperm_itemid* to identify a item that the permission applies to.
The permissions are further identified by the mid of the module the permission relates to,
and the groupid the permission applies to.

This helper streamlines using permissions by automatically using module and group information
that can be inferred.

`Xmf\Module\Helper\Permission` extends [Xmf\Module\Helper\AbstractHelper](abstracthelper.php).

### new Permission(*$dirname*)

Creates the permission helper for the module specified by name as *$dirname*.
If the string *$dirname* is empty, the current module in XOOPS will be user.

### checkPermission(*$gperm_name*, *$gperm_itemid*, *$trueifadmin*)

Check if the user has the permission named *$gperm_name* for the item identified by *$gperm_itemid*.

Normally an admin user always has permission. If *$trueifadmin*, an optional boolean, is
specified as *false*, the admin user's permissions will be checked like any normal user.

Returns true if the user has the permission, otherwise false.

### checkPermissionRedirect(*$gperm_name*, *$gperm_itemid*, *$url*, *$time*, *$message*, *$trueifadmin*)

Check if the user has the permission named *$gperm_name* for the item identified by *$gperm_itemid*.
If not, the session will be redirected to the module relative URL specified in *$url* with the
message in *$message*.

### getGroupsForItem(*$gperm_name*, *$gperm_itemid*)

Get array of groups granted permissions for the permission named *$gperm_name* for the item
identified by *$gperm_itemid*.

Normally an admin user always has permission. If *$trueifadmin*, an optional boolean, is
specified as *false*, the admin user's permissions will be checked like any normal user.

Returns an array of integer group ids.

### savePermissionForItem(*$gperm_name*, *$gperm_itemid*, *$groups*)

Grant the permission named *$gperm_name* for the item identified by *$gperm_itemid* to all of the
groups identified in the array *$groups*.

### deletePermissionForItem(*$gperm_name*, *$gperm_itemid*)

Delete the permission named *$gperm_name* for the item identified by *$gperm_itemid* for all groups.

Alternately, *$gperm_name* can be an array of permission names, and all the named permissions for the
specified item will be deleted for all groups.

The intended use of this method is to in response to the item *$gperm_itemid* being deleted.

public object
### getGroupSelectFormForItem(*$gperm_name*, *$gperm_itemid*, *$caption*, *$name*, *$include_anon*, *$size*, *$multiple*)

Creates a XoopsFormSelectGroup form element to select groups with permission to a specific
*$gperm_name* and *$gperm_itemid*.  The form element will be preset with existing permissions.

The caption for the element is specified in *$caption*.

If the name *$name* is empty or omitted, a default name created by `defaultFieldName()` will be used.

Set *$include_anon* (default false) to true to include the anonymous group.
The size in *$size* (default 5) sets number of vertical rows shown in the element.
If *$multiple* (default true) is true, multiple groups can be assigned to the permission.

### defaultFieldName(*$gperm_name*, *$gperm_itemid*)

Generate a default name to be used for the XoopsFormSelectGroup based on *$gperm_name* and *$gperm_itemid*.

If you do not specify the name in `getGroupSelectFormForItem()` this allows you to determine the
element name to retrieve the user input.

Returns a string.
