## Using the Permission Helper

XOOPS has a powerful and flexible permission system based on users' membership in groups.
This privilege mechanism allows you to associate a group with module, permission name and item_id.
So checking a user's privilege requires finding out their assigned groups, looking up the module id,
and using that to look up a name and id.

If that sounds complicated and filled with the potential for error, don't worry. XMF offers simple
solutions for the most needed actions.

A *permission helper* is a module aware helper used for simple access to the most common permission
needs. It assumes that we are checking the privilege for the current user, and the module specified
when we instantiate the permission helper. If we don't supply a module name, it will assume ues the
current module by default. After that, all the module programmer has to supply is the name and id
of the item.

