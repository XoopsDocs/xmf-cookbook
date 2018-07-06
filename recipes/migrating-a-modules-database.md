# Migrating a Module's Database

Over time, a module can accumulate numerous database changes. For simple situations, where there are a small set of known changes, the [Tables](altering-database-tables.md) class may be an appropriate solution. For larger change sets, possibly spanning multiple generations or versions of a module, determining which changes need to be applied quickly becomes the most serious concern. `Xmf\Database\Migrate` assists in solving this problem by comparing the existing tables against a prepared schema description and generating the needed data definition language \(DDL\) statements to convert the existing tables to the target schema definition.

The automated migration DDL fully handles situations such adding or dropping tables or columns, as well as changing column attributes, such as type, length or default value. Indexes are also synchronized.

For more complex requirements, such as renaming tables or columns, and data conversion, it is possible to manually specify DDL or SQL statements that will be run prior to the automatic synchronization.

## Basics

Tables must be declared in your module's xoops\_version.php file. The `$modversion['tables']` entry should be an array of table names. This is an existing standard for all XOOPS modules, an this note is simply to reinforce that _Migrate_ depends on this information.

Typically, a database is initially prepared through a database tool, such as phpMyAdmin, MySQL Workbench or other interactive modeling tool. Once the database is defined, we can generate Migrate's internal schema representation to use in migrating any existing tables. For existing modules, the schema can be prepared from the tables it creates.

Directly editing a generated schema representation is NOT recommended. The schema generation and comparison are closely related, and direct changes may result in tables that work correctly, but appear to need updated on each comparison.

For simple situations, you can use [Xmf\Database\Migrate](../reference/database/migrate.md) directly. For more involved migrations, it is best to extend `Migrate` with your own module specific class to take full advantage of the available features.

## Generate a Schema Definition

To generate a schema definition from your existing tables, instantiate a `Migrate` object, passing it your module's directory name \(dirname.\) Then, invoke the `saveCurrentSchema()` method.

This will save a schema file to the module's **sql** directory. The file is named based on the dirname and the module's version.

```php
    $migrate = new Xmf\Database\Migrate('mymodule');
    $result = $migrate->saveCurrentSchema();
    if (false === $result) {
        // the schema was not saved, handle the error condition
    }
```

## Basic Synchronization

To synchronize any existing table to a stored scheme definition takes only one call to `synchronizeSchema()`.

This can add and drop tables, add and drop columns, and add and drop indexes.

```php
function xoops_module_update_mymodule(XoopsModule $module)
{
    $migrate = new Xmf\Database\Migrate('mymodule');
    $result = $migrate->synchronizeSchema();
    return true;
}
```

## Rename a Set of Tables

Naming conventions have changed over time, so preparing an older set of tables to use with a new software version often requires checking to see if renaming is needed, and conditionally renaming the existing tables.

In this scenario we will rename the tables in _newbb_ to conform to module standards that the table name begin with the module name and an underscore.

Migrate can easily handle dropping and adding columns, tables and indexes. Migrate can't automatically handle renaming a table or column. To `synchronizeSchema()` a renamed column looks just like a dropped column and a added column. To resolve this ambiguity, we need to explicitly rename entities in our custom class that extends Migrate.

For this, we will extend `Migrate` and take advantage of the `preSyncActions()` hook. By doing these changes _before_ the synchronization, we can make all the needed changes in one pass. We created a schema file using the new names that is distributed with the module, so once the tables are renamed, we can synchronize any other changes.

Migrate automatically gives us an instance of [Xmf\Database\Tables](../reference/database/tables/) and we can add any extra commands we need.

```php
class NewbbMigrate extends Xmf\Database\Migrate
{
    // a array of 'old_name' => 'new_name' pairs
    private $renameTables = array(
        'bb_archive'     => 'newbb_archive',
        'bb_categories'  => 'newbb_categories',
        'bb_votedata'    => 'newbb_votedata',
        'bb_forums'      => 'newbb_forums',
        'bb_posts'       => 'newbb_posts',
        'bb_posts_text'  => 'newbb_posts_text',
        'bb_topics'      => 'newbb_topics',
        'bb_online'      => 'newbb_online',
        'bb_digest'      => 'newbb_digest',
        'bb_report'      => 'newbb_report',
        'bb_attachments' => 'newbb_attachments',
        'bb_moderates'   => 'newbb_moderates',
        'bb_reads_forum' => 'newbb_reads_forum',
        'bb_reads_topic' => 'newbb_reads_topic',
        'bb_type'        => 'newbb_type',
        'bb_type_forum'  => 'newbb_type_forum',
        'bb_stats'       => 'newbb_stats',
        'bb_user_stats'  => 'newbb_user_stats',
    );

    /**
     * NewbbMigrate constructor.
     */
    public function __construct()
    {
        parent::__construct('newbb');
    }

    /**
     * change table prefix if needed
     */
    private function changePrefix()
    {
        foreach ($this->renameTables as $oldName => $newName) {
            if ($this->tableHandler->useTable($oldName)) {
                $this->tableHandler->renameTable($oldName, $newName);
            }
        }
    }

    /**
     * Perform any upfront actions before synchronizing the schema
     *
     * @return void
     */
    protected function preSyncActions()
    {
        // change 'bb' table prefix to 'newbb'
        $this->changePrefix();
    }
}
```

We kick this off with this function in our `$modversion['onUpdate']` file. We use the pre\_update function, so that we change the tables to the correct names before any other update processing.

```php
function xoops_module_pre_update_newbb(XoopsModule $module)
{
    XoopsLoad::load('migrate', 'newbb');
    $newbbMigrate = new NewbbMigrate();
    $newbbMigrate->synchronizeSchema();

    return true;
}
```

## Convert a Changed Column

Let's extend the previous example and suppose we also want to convert an IP Address column to handle IPv6 addresses as part of the migration. The old column was integer, with the addresses in network form, but we are changing to a varchar column, with the address in a human readable form.

```php
class NewbbMigrate extends Xmf\Database\Migrate
{
    // a array of 'old_name' => 'new_name' pairs
    private $renameTables = array(
        'bb_archive'     => 'newbb_archive',
        'bb_categories'  => 'newbb_categories',
        'bb_votedata'    => 'newbb_votedata',
        'bb_forums'      => 'newbb_forums',
        'bb_posts'       => 'newbb_posts',
        'bb_posts_text'  => 'newbb_posts_text',
        'bb_topics'      => 'newbb_topics',
        'bb_online'      => 'newbb_online',
        'bb_digest'      => 'newbb_digest',
        'bb_report'      => 'newbb_report',
        'bb_attachments' => 'newbb_attachments',
        'bb_moderates'   => 'newbb_moderates',
        'bb_reads_forum' => 'newbb_reads_forum',
        'bb_reads_topic' => 'newbb_reads_topic',
        'bb_type'        => 'newbb_type',
        'bb_type_forum'  => 'newbb_type_forum',
        'bb_stats'       => 'newbb_stats',
        'bb_user_stats'  => 'newbb_user_stats',
    );

    /**
     * NewbbMigrate constructor.
     */
    public function __construct()
    {
        parent::__construct('newbb');
    }

    /**
     * change table prefix if needed
     */
    private function changePrefix()
    {
        foreach ($this->renameTables as $oldName => $newName) {
            if ($this->tableHandler->useTable($oldName)) {
                $this->tableHandler->renameTable($oldName, $newName);
            }
        }
    }

    /**
     * Change integer IPv4 column to varchar IPv6 capable
     *
     * Convert to int to big int, and adjust for signed conversion, 
     * then convert to varchar and run INET_NTOA conversion
     *
     * @param string $tableName  table to convert
     * @param string $columnName column with IP address
     *
     * @return void
     */
    private function convertIPAddresses($tableName, $columnName)
    {
        if ($this->tableHandler->useTable($tableName)) {
            $attributes = $this->tableHandler->getColumnAttributes($tableName, $columnName);
            if (false !== strpos($attributes, ' int(')) {
                if (false === strpos($attributes, 'unsigned')) {
                    $this->tableHandler->alterColumn($tableName, $columnName, " bigint(16) NOT NULL  DEFAULT '0' ");
                    $this->tableHandler->update(
                        $tableName,
                        array($columnName => "4294967296 + $columnName"),
                        "WHERE $columnName < 0",
                        false
                    );
                }
                $this->tableHandler->alterColumn($tableName, $columnName, " varchar(45)  NOT NULL  DEFAULT '' ");
                $this->tableHandler->update($tableName, array($columnName => "INET_NTOA($columnName)"), '', false);
            }
        }
    }

    /**
     * Perform any upfront actions before synchronizing the schema
     *
     * @return void
     */
    protected function preSyncActions()
    {
        // change 'bb' table prefix to 'newbb'
        $this->changePrefix();
        // Convert IP address columns from int to readable varchar(45) for IPv6
        $this->convertIPAddresses('newbb_posts', 'poster_ip');
    }
}
```

