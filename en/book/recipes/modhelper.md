## Introducing Module Helpers

The module helper is an easy way to access module related information, such as configurations,
handlers and more. Using the module helper can simplify your code.

### Simplify Reading Module Configs
Consider the common task of getting a configuration value for a module. This can get more complicated
if you need this in a circumstance where your module is not the currently active module.

Here is an example of how this is done now. We have a module named “bar” and we want to get
the configuration “foo”:

```
$module_handler = xoops_gethandler('module');
$module         = $module_handler->getByDirname('bar');
$config_handler = xoops_gethandler('config');
$moduleConfig   = $config_handler->getConfigsByCat(0, $module->getVar('mid'));
$value = (isset($moduleConfig['foo']) ? $moduleConfig['foo'] : 'baz';
echo "The value of 'foo' being used is: " . $value;
```

Here is an XMF version that accomplishes the same thing:

```
$helper = \Xmf\Module\Helper::getHelper('bar');
echo "The value of 'foo' being used is: " . $helper->getConfig('foo', 'baz');
```

### Easy Access to Module Object

Here, we extend the last example to get the module's version using our XMF module helper.

```
$version = $helper->getModule()->getVar('version');
```

See the reference section for [Xmf\Module\Helper](../module/helper.md) for more about the module helper.
