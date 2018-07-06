# Checking Permissions

Checking a user's permissions is easy with a permission helper.

The first step is to get a Permission Helper instance.

```php
$permHelper = new \Xmf\Module\Helper\Permission();
```

## Does the User Have Permission for an Item?

Let's imagine we have a protected forum, where each topic is protected by group permissions. The user needs a 'viewtopic' permission for a topic to view it. The id of the forum is stored in $id.

```php
$permission = $permHelper->checkPermission('viewtopic', $id);
```

The $permission variable now holds true if the user has permission, false if not.

## Leave if the User Does Not Have Permission

This is based on the same scenario as above, but we want to send the user back to the index page, if they don't have permission.

```php
$permHelper->checkPermissionRedirect('viewtopic', $id,
             'index.php', 3, 'You are not allowed to view that topic');
```

The user's browser session will be redirected to the module's index.php if the required permission is not assigned.

