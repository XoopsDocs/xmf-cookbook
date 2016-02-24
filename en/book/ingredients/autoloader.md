## Autoloading

You never need to use XoopsLoad or manually load a class file to use XMF. All XMF classes load automatically
whenever you refer to them.

For example, consider the familiar XoopsRequest class.

```
XoopsLoad('xoopsrequest');
$cleanInput = XoopsRequest::getString('input', '');
```

XMF has a version of Request that is regularly synchronized with newer versions, and will be the
definitive version starting with XOOPS 2.5.8. This is how the same code can look with XMF:

```
$input = Xmf\Request::getString('input', '');
```

You can combine this with the tips under [namespaces](namespaces.md), and expand to a few more input fields
for a look at a more typical use case:

```
use Xmf\Request;

// ...

$input = Request::getString('input', '');
$id = Request::getInt('id', '');
$op = Request::getCmd('op', 'display');
```

Autoloading for the `Xmf` namespace is managed by a [PSR-4](http://www.php-fig.org/psr/psr-4/) autoloader.
The same autoloader also manages autoload for several libraries that XMF depends on. This autoloader will
be standard in future XOOPS versions.
