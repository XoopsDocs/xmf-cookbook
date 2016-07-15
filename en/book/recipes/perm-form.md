## Managing Item Permissions

For item permissions to work, we have to be able to assign permissions to an item. The
[XMF permission helper](perm-check.md) makes this simple.

The first step is to get a Permission Helper instance.

```php
$permHelper = new \Xmf\Module\Helper\Permission();
```

### Assign Permissions to an Item From a Form

For this example, we will assume that we build a XoopsForm object, *$form*, where a topic item can be edited,
and we want to assign group permissions for a permission named *'viewtopic'* on that form.
The topic id is in in the variable *$id*.
We will also assume that our module directory is *'forum'*.

Here is the code that adds our group selection for permissions to our form:

```php
// … build a form …

$form->addElement($permHelper->getGroupSelectFormForItem('viewtopic', $id,
    'Groups with View Topic Permission'));

// … continue to build form and present it …
```

The permission selection will be pre-populated with existing group permissions. The field name will be
generated automatically if not specified from the module directory, the permission name and the item id,
In this example, it might look something like this 'forum_viewtopic_12'. We can ask the for the name
whenever we need it, so the exact format isn't important. If needed, you can specify your own name and
several other options if needed. For more on these options, see the reference section on
[Xmf\Module\Helper\Permission](../module/permission.md).

Here is code that saves our group permissions from the form when it is submitted.

```php
// … process form input …

$name=$permHelper->defaultFieldName('viewtopic', $id);
$groups=\Xmf\Request::getArray($name, array(), 'POST');
$permHelper->savePermissionForItem('viewtopic', $id, $groups);

// … continue to process form …
```

We've added group permissions to a form, and saved those permissions to the database with 5 lines of XMF.

### Clean Up Permissions When an Item is Deleted

If a permission protected item is deleted, it is important to delete all of the permissions
that may have been assigned. It is important to delete by name and id. If you have more than
one entity protected, you might have duplicate ids. For example, a category and a topic might
both have view and post permissions. The name implies which entity the id applies to.

Here is an example of cleaning up when deleting a topic. The topic id is in $id.

```php
$permHelper->deletePermissionForItem('viewtopic', $id);
```

For the more complicated case, we may have more that one permission name to clean up.
Assuming we also have a permissions name 'posttopic' that applies to the topic id.
Of course, we could just issue a separate `deletePermissionForItem()` for each one.
We can also specify it like this:

```php
$permissionNames = array('posttopic', 'viewtopic');
$permHelper->deletePermissionForItem($permissionNames, $id);
```

The XMF permission helper can help streamline your permission coding, so you can
concentrate on user experience rather than the internal mechanics.
