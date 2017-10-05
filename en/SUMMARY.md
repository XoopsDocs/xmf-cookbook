# Table of Contents

* [Basic Ingredients](book/ingredients/README.md)
    * [Namespaces](book/ingredients/namespaces.md)
    * [Autoloading](book/ingredients/autoloader.md)
    * [Debugging](book/ingredients/debugging.md)
    * [Forward Compatibility](book/ingredients/compatibility.md)
* [Recipes](book/recipes/README.md)
    * [Introducing Module Helpers](book/recipes/modhelper.md)
        * Simplify Reading Module Configs
        * Easy Access to Module Object
    * [Using the Permission Helper](book/recipes/permission.md)
        * [Checking Permissions](book/recipes/perm-check.md)
            * Does the User Have Permission for an Item?
            * Leave if the User Does Not Have Permission
        * [Managing Item Permissions](book/recipes/perm-form.md)
            * Assign Permissions to an Item From a Form
            * Clean Up Permissions When an Item is Deleted
    * [Using the Session Helper](book/recipes/session.md)
        * Save and Retrieve Context
    * [Use JSON Web Tokens](book/recipes/jsonwebtokens.md)
        * Ajax Protection with JWT
    * [Altering Database Tables](book/recipes/dbtables.md)
        * Rename a Database Table
        * Add a Column to a Table
    * [Migrating a Module's Database](book/recipes/migrations.md)
        * Generate a Schema Definition
        * Basic Synchronization
        * Rename a Set of Tables
        * Convert a Changed Column
    * [Loading Initial Data](book/recipes/loaddata.md)
        * Simple Table Loading
        * Apply a Transform
        * Save Table Data in YAML
        * Case Study
    * [Module Admin Pages](book/recipes/modadmin.md)
        * [Hide and Seek with Icons](book/recipes/modadm-icons.md)
            * Where are the icons?
            * menu.php icons
        * [Standard Admin Pages](book/recipes/modadm-pages.md)
            * index.php conversion
            * pages.php conversion
    * [Manage Metadata](book/recipes/metagen.md)
        * SEO Slugs
        * Generate a Teaser
        * Generate Keyword Lists
        * Generate a Search Summary
    * [Highlighting Content](book/recipes/highlight.md)
* [Reference](book/reference/README.md)
    * [Assert](book/assert/README.md)
        * [Assertions](book/assert/assert.md)
    * [Database](book/database/README.md)
        * [Migrate](book/database/migrate.md)
        * [TableLoad](book/database/tableload.md)
        * [Tables](book/database/tables.md)
            * [Getting Started](book/database/tables-start.md)
            * [Table Operations](book/database/tables-tableops.md)
            * [Working with Columns](book/database/tables-columns.md)
            * [Working with Indexes](book/database/tables-indexes.md)
            * [Changing Table Data](book/database/tables-data.md)
            * [Interacting with the Work Queue](book/database/tables-queue.md)
            * [Error Info and Debugging](book/database/tables-errors.md)
    * [Debug](book/debug/README.md)
    * [FilterInput](book/filterinput/README.md)
    * [Highlighter](book/highlighter/README.md)
    * [IPAddress](book/ipaddress/README.md)
    * [Jwt](book/jwt/README.md)
        * [JsonWebToken](book/jwt/jsonwebtoken.md)
        * [KeyFactory](book/jwt/keyfactory.md)
        * [TokenFactory](book/jwt/tokenfactory.md)
        * [TokenReader](book/jwt/tokenreader.md)
    * [Key](book/key/README.md)
        * [ArrayStorage](book/key/arraystorage.md)
        * [Basic](book/key/basic.md)
        * [FileStorage](book/key/filestorage.md)
        * [KeyAbstract](book/key/keyabstract.md)
        * [StorageInterface](book/key/storageinterface.md)
    * [Language](book/language/README.md)
    * [Metagen](book/metagen/README.md)
        * [Extracting Data](book/metagen/generating.md)
        * [Applying Data](book/metagen/applying.md)
    * [Module](book/module/README.md)
        * [Admin](book/module/admin.md)
        * [Helper](book/module/helper.md)
        * [Helper](book/module/helper-ns.md)
            * [AbstractHelper](book/module/abstracthelper.md)
            * [Cache](book/module/cache.md)
            * [GenericHelper](book/module/generichelper.md)
            * [Permission](book/module/permission.md)
            * [Session](book/module/session.md)
    * [Random](book/random/README.md)
    * [Request](book/request/README.md)
    * [StopWords](book/stopwords/README.md)
    * [Uuid](book/uuid/README.md)
    * [Yaml](book/yaml/README.md)
* [Credits](book/credits.md)
