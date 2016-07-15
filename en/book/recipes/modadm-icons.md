## Win Hide and Seek with Icons

As XOOPS matures, the icons won't be in the same place. There are static methods in
[Xmf\Module\Admin](..\module\admin.md) to help you win the game of hide and seek once and for all.


### Where are the icons?

You might have had some code that looks like this:

```php
$dirname         = basename(dirname(dirname(__FILE__)));
$module_handler  = xoops_gethandler('module');
$module          = $module_handler->getByDirname($dirname);
$pathIcon16      = $module->getInfo('icons16');
$img_src         = $pathIcon16 . '/delete.png';
```

Here is an XMF version that accomplishes the same thing, in a migration ready way:

```php
$img_src = \Xmf\Module\Admin::iconUrl('delete.png', 16);
```

You can also specify 32 for the size to get the larger size. And you don't have to worry about where the
system icon library is hiding this time, as you will get back a full URL.

### menu.php

Administration area menus are one place where icon location changes cause problems.

Here is an example of an old menu.php:

```php
$dirname = basename(dirname(dirname(__FILE__)));
$module_handler = xoops_gethandler('module');
$module = $module_handler->getByDirname($dirname);
$pathIcon32 = $module->getInfo('icons32');

$adminmenu=array();
// Index
$adminmenu[] = array(
	'title'	=> _MI_DEMO_ADMIN_INDEX ,
	'link'	=> 'admin/index.php' ,
	'icon'	=> '../../' . $pathIcon32 . '/home.png'
) ;
// About
$adminmenu[] = array(
	'title'	=> _MI_DEMO_ADMIN_ABOUT ,
	'link'	=> 'admin/about.php' ,
	'icon'	=> '../../' . $pathIcon32 . '/about.png'
) ;
```

Here is a sample of how we can rewrite menu.php to work now and later with XMF.

```php
// get path to icons
$pathIcon32='';
if (class_exists('Xmf\Module\Admin', true)) {
    $pathIcon32 = \Xmf\Module\Admin::menuIconPath('');
}

$adminmenu=array();
// Index
$adminmenu[] = array(
	'title'	=> _MI_DEMO_ADMIN_INDEX ,
	'link'	=> 'admin/index.php' ,
	'icon'	=> $pathIcon32.'home.png'
) ;
// About
$adminmenu[] = array(
	'title'	=> _MI_DEMO_ADMIN_ABOUT ,
	'link'	=> 'admin/about.php' ,
	'icon'	=> $pathIcon32.'about.png'
) ;
```
