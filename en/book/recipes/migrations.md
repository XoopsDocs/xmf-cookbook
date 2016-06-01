## Migrating a Database

As a module grows, so does its database requirements. There have been many strategies to deal with
the inevitable database changes, from custom .sql files to handwritten queries. `Xmf\Database\Tables`
is an object oriented approach to a standard solution to this common problem.

### Rename a Database Table

This scenario references a module called 'pedigree' and we are going to define an update function
that will rename an old table named 'eigenaar' to a standardized name of 'pedigree_owner'.

First, the old way:

```php
function tableExists($tablename)
{
    global $xoopsDB;
    $result=$xoopsDB->queryF("SHOW TABLES LIKE '$tablename'");
    return($xoopsDB->getRowsNum($result) > 0);
}

function xoops_module_update_pedigree()
{
    global $xoopsDB;

    if (tableExists($xoopsDB->prefix('eigenaar'))) {
        $sql = sprintf(
            'ALTER TABLE ' . $xoopsDB->prefix('eigenaar')
          . ' RENAME ' . $xoopsDB->prefix('pedigree_owner')
        );
        $result = $xoopsDB->queryF($sql);
        if (!$result) {
            echo '<br />' . _AM_PED_UPGRADEFAILED
                 . ' ' . _AM_PED_UPGRADEFAILED2;
            $errors++;
        }
    }
    return TRUE;
}
```

Here is the same operation using the \Xmf\Database\Tables class:

```php
function xoops_module_update_pedigree()
{
    $migrate = new \Xmf\Database\Tables();
    if($migrate->useTable('eigenaar')) { // if this returns false, there is no table
        $migrate->renameTable('eigenaar', 'pedigree_owner');
        if(!$migrate->executeQueue()) {
	        echo '<br />' . _AM_PED_UPGRADEFAILED  . ' ' . $migrate->getLastError();
	    }
    }
}
```

### Add a Column to a Table

Let's extend the previous example and suppose we also want to add a column, named
'registrar_code', as a varchar(24) at the same time. Here is the new function:

```php
function xoops_module_update_pedigree()
{
    $migrate = new \Xmf\Database\Tables();
    if($migrate->useTable('eigenaar')) {
        $migrate->renameTable('eigenaar', 'pedigree_owner');
        $migrate->addColumn('pedigree_owner', 'registrar_code', "varchar(24) NOT NULL DEFAULT ''");
        if(!$migrate->executeQueue()) {
	        echo '<br />' . _AM_PED_UPGRADEFAILED  . ' ' . $migrate->getLastError();
	    }
    }
}
```

### Going Further

There are methods available to handle any needed table changes. Tables can be created, dropped,
and altered. You can modify multiple tables in one pass. All modifications go into a queue, so you
can halt the entire process easily if you find something is amiss. Refer to the reference
documentation for [Xmf\Database\Tables](../database/tables.md) for details.

There is a companion object, [Xmf\Database\TableLoad](../database/tableload.md), to assist in
adding data to tables, too.

It is worth considering these classes whenever you need to add or modify tables for your module.
