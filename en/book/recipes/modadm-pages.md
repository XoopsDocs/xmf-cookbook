# modadm-pages

The next generation `Xoops\Module\Admin` makes a few changes to the module administration class methods. With [Xmf\Module\Admin](../module/admin.md) you can begin using the new methods now for forward compatibility.

Here are examples of the standard index and about pages.

## index.php

An example index page in the current 2.5 format:

```php
$indexAdmin = new ModuleAdmin();

echo $indexAdmin->addNavigation('index.php');
echo $indexAdmin->renderIndex();
```

Forward compatible version using XMF:

```php
$indexAdmin = \Xmf\Module\Admin::getInstance();

$indexAdmin->displayNavigation('index.php');
$indexAdmin->displayIndex();
```

## about.php

An example about page in the current 2.5 format:

```php
$aboutAdmin = new ModuleAdmin();

echo $aboutAdmin->addNavigation('about.php');
echo $aboutAdmin->renderAbout('6XYZRW5DR3VTJ', false);
```

Migration ready using XMF:

```php
$aboutAdmin = \Xmf\Module\Admin::getInstance();

$aboutAdmin->displayNavigation('about.php');
\Xmf\Module\Admin::setPaypal('6XYZRW5DR3VTJ');
$aboutAdmin->displayAbout(false);
```

Note the setPaypal\(\) call. In the next generation, PayPal information is set in xoops\_version.php instead as a parameter to renderAbout\(\). The call satisfies the requirements in 2.5 systems, and will cause no harm in later versions, but accomplish nothing.

Use these examples and apply the concepts to any other administration scripts your module uses to make them forward compatible, too.

