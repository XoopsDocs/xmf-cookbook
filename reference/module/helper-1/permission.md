# Permission

The `Xmf\Module\Helper\Permission` class is a module aware helper for simplified access to system group permissions in a module.

System group permissions use a string _$gperm\_name_ as a permission name, and an integer _$gperm\_itemid_ to identify a item that the permission applies to. The permissions are further identified by the mid of the module the permission relates to, and the groupid the permission applies to.

This helper streamlines using permissions by automatically using module and group information that can be inferred.

`Xmf\Module\Helper\Permission` extends [Xmf\Module\Helper\AbstractHelper](https://github.com/xoops/xmf-cookbook/tree/2971b4bb568db7c6791e293e50ffc917d75ed81f/en/book/module/abstracthelper.php).

## new Permission\(_$dirname_\)

Creates the permission helper for the module specified by name as _$dirname_. If the string _$dirname_ is empty, the current module in XOOPS will be user.

## checkPermission\(_$gperm\_name_, _$gperm\_itemid_, _$trueifadmin_\)

Check if the user has the permission named _$gperm\_name_ for the item identified by _$gperm\_itemid_.

Normally an admin user always has permission. If _$trueifadmin_, an optional boolean, is specified as _false_, the admin user's permissions will be checked like any normal user.

Returns true if the user has the permission, otherwise false.

## getItemIds(_$gperm\_name_, _$gperm\_groupid_)

Returns an array of items for which the group(s) specified in _$gperm\_groupid_ have the permission named in _$gperm\_name_.

## checkPermissionRedirect\(_$gperm\_name_, _$gperm\_itemid_, _$url_, _$time_, _$message_, _$trueifadmin_\)

Check if the user has the permission named _$gperm\_name_ for the item identified by _$gperm\_itemid_. If not, the session will be redirected to the module relative URL specified in _$url_ with the message in _$message_.

## getGroupsForItem\(_$gperm\_name_, _$gperm\_itemid_\)

Get array of groups granted permissions for the permission named _$gperm\_name_ for the item identified by _$gperm\_itemid_.

Normally an admin user always has permission. If _$trueifadmin_, an optional boolean, is specified as _false_, the admin user's permissions will be checked like any normal user.

Returns an array of integer group ids.

## savePermissionForItem\(_$gperm\_name_, _$gperm\_itemid_, _$groups_\)

Grant the permission named _$gperm\_name_ for the item identified by _$gperm\_itemid_ to all of the groups identified in the array _$groups_.

## deletePermissionForItem\(_$gperm\_name_, _$gperm\_itemid_\)

Delete the permission named _$gperm\_name_ for the item identified by _$gperm\_itemid_ for all groups.

Alternately, _$gperm\_name_ can be an array of permission names, and all the named permissions for the specified item will be deleted for all groups.

The intended use of this method is to in response to the item _$gperm\_itemid_ being deleted.

public object

## getGroupSelectFormForItem\(_$gperm\_name_, _$gperm\_itemid_, _$caption_, _$name_, _$include\_anon_, _$size_, _$multiple_\)

Creates a XoopsFormSelectGroup form element to select groups with permission to a specific _$gperm\_name_ and _$gperm\_itemid_. The form element will be preset with existing permissions.

The caption for the element is specified in _$caption_.

If the name _$name_ is empty or omitted, a default name created by `defaultFieldName()` will be used.

Set _$include\_anon_ \(default false\) to true to include the anonymous group. The size in _$size_ \(default 5\) sets number of vertical rows shown in the element. If _$multiple_ \(default true\) is true, multiple groups can be assigned to the permission.

## defaultFieldName\(_$gperm\_name_, _$gperm\_itemid_\)

Generate a default name to be used for the XoopsFormSelectGroup based on _$gperm\_name_ and _$gperm\_itemid_.

If you do not specify the name in `getGroupSelectFormForItem()` this allows you to determine the element name to retrieve the user input.

Returns a string.

