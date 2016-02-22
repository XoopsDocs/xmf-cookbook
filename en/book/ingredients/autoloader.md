## Autoloading

You never need to use XoopsLoad or manually load a class file to use XMF. All XMF classes load automatically
whenever you refer to them.

For example, consider the familiar XoopsRequest class.

```
XoopsLoad('xoopsrequest');
$cleanInput = XoopsRequest::getString('input', '');
```

XMF has a version of Request. (*It actually has had Request longer than XOOPS, it just had not been released.*)
This is how it looks with XMF:

```
$input = Xmf\Request::getString('input', '');
```

Combine this with the tips under namespaces, and expand to a few more input fields:

```
use Xmf\Request;

// more code ...

$input = Request::getString('input', '');
$id = Request::getInt('id', '');
$op = Request::getCmd('op', 'display');
```

