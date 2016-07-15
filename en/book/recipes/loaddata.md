## Loading Initial Data

It is a common need to insert data into a table when installing or updating a module.
`Xmf\Database\TableLoad` has several methods that provide a standard solution to this common problem.

Presently, this task is usually handled with a file of raw SQL inserts fed to a
`queryFromFile()` function. This method has some drawbacks. For an example, consider
this line from a language specific file used in the installation of XOOPS:

```SQL
INSERT INTO ranks VALUES (1, 'Just popping in', 0, 20, 0, 'ranks/rank3e632f95e81ca.gif');
```

SQL INSERTS are a way to talk to the database, they are not a good way work with data.
There is no practical way to manipulate the data before inserting. The `queryFromFile()` function
applies the prefix to the table names. Creating the SQL INSERTS requires removal of those prefixes,
often a manual process.

To provide a locale specific translation, the SQL file must be translated. This requires translators
to edit the SQL dump instead of working in standard translation formats. As a result, any changes
to the underlying tables also require tracking down and visiting each language specific file.

If instead of SQL INSERTS, we keep the data in a PHP accessible data format, we can manipulate it as data,
applying transforms as needed, we keep the table awareness in our module, where it belongs, instead of
spreading it in to many unrelated places.

There is the area where [Xmf\Database\TableLoad](../database/tableload.md) can assist.


### Simple Table Loading

Storing the data as a YAML document makes it easy to manipulate. The row data from our example above would
look like this:

```YAML

-
  rank_id: 1
  rank_title: "Just popping in"
  rank_min: 0
  rank_max: 20
  rank_special: 0
  rank_image: "ranks/rank3e632f95e81ca.gif"
```

If the rows are saved in YAML form in a file, loading it into the database is a single line:

```PHP
\Xmf\Database\TableLoad::loadTableFromYamlFile('ranks', 'ranks-data.yml');
```


### Apply a Transform

You can also load data directly from an array, using TableLoad::loadTableFromArray().

Take the file describe in the previous step, and load it to an array using [Xmf\Yaml](../yaml/README.md).

```php
    $data = Yaml::readWrapped(ranks-data.yml');
```

Now, we can work with the data, changing it before inserting it. We will assume your application
provides a translate() function to return a localized string for the title.

```php
    foreach ($data as $index => $row) {
        $data[$index]['rank_title'] = translate($data[$index]['rank_title']);
    }
    TableLoad::loadTableFromArray('ranks', $data);
```

### Save Table Data in YAML

OK, it is easy to load, but how do you get the data in YAML format? Well, phpMyAdmin offers YAML export,
but we also have a solution in `TableLoad`.

```PHP
\Xmf\Database\TableLoad::saveTableToYamlFile('ranks', 'ranks-data.yml');
```

You can use whatever tools you need to craft the initial data in your database, and then use this
single line to save the whole table to a file in YAML form.

### Case Study

Sometimes the need is more complex than straight saving and loading. For this case study we will
look at how we can simplify the Help Pages feature in the *gwiki* module. In this case, we have
a set of help pages that can optionally be loaded into the wiki by the administrator. The administrator
can also reload the stock help pages if needed, replacing any local changes.

Since the pages are optional, we cannot count on starting with an empty table. We can't force the
auto-increment id column.

Also, pages can exist both as an active page and as multiple inactive pages as revision histories.

Using the SQL INSERT method in this circumstance was awkward and time consuming. Revising the Help Pages
for the distribution was something to be avoided. That does not help to improve the product quality!

With `TableLoad` extracting a fresh revision of the help pages is this simple:

```PHP
$criteria = new CriteriaCompo(new Criteria('page_set_home', 'Help:Index', '='));
$criteria->add(new Criteria('active', '1', '='), 'AND');
$skipColumns = array('gwiki_id');
$status = TableLoad::saveTableToYamlFile('gwiki_pages', 'helppages.yml', $criteria, $skipColumns);
```

We create a `Criteria` object to define the data we want, define the id column we want to *not* include,
and save it.

Loading is also more complicated, as we need to mark any existing help pages as inactive. For this,
in this case, we will use the `update()` method from our [Xmf\Database\Tables](migrations.md)
companion class.


```PHP
    $criteria = new Criteria('page_set_home', 'Help:Index', '=');
    if (0 < TableLoad::countRows('gwiki_pages', $criteria)) {
        $migrate = new Tables();
        $values = array('active' => '0');
        $migrate->useTable('gwiki_pages');
        $migrate->update('gwiki_pages', $values, $criteria);
        $migrate->executeQueue(true);
    }
    $result = TableLoad::loadTableFromYamlFile('gwiki_pages', 'helppages.yml');
```

Establish criteria, set the active column, execute an update, then load the new data.

If your module requires initializing tables with data, [Xmf\Database\TableLoad](../database/tableload.md)
is a useful tool to keep in mind.
