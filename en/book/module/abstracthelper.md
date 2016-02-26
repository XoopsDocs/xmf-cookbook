## AbstractHelper

The `Xmf\Module\Helper\AbstractHelper` abstract class is the base class for module aware helpers.

### __construct(*$dirname*)

Instantiate a XoopsModule object for the helper to use. If the string *$dirname* is empty, the current
module in XOOPS will be user. Otherwise, it will attempt to load the module by name.

### init()

init() is called by the construct after the appropriate XoopsModule object is loaded.

### setDebug(*$bool*)

Set debug option for the helper on (*true*) or off (*false*.)
The default for *$bool*, if not specified, is *true*.

### addLog(*$log*)

Add the message string *$log* to the module log.

