# AbstractHelper

The `Xmf\Module\Helper\AbstractHelper` abstract class is the base class for module aware helpers.

## \_\_construct\(_$dirname_\)

Instantiate a XoopsModule object for the helper to use. If the string _$dirname_ is empty, the current module in XOOPS will be user. Otherwise, it will attempt to load the module by name.

## init\(\)

init\(\) is called by the constructor after the appropriate XoopsModule object is loaded.

## dirname\(\)

Returns the module dirname associated with the helper.

## setDebug\(_$bool_\)

Set debug option for the helper on \(_true_\) or off \(_false_.\) The default for _$bool_, if not specified, is _true_.

## addLog\(_$log_\)

Add the message string _$log_ to the module log.

