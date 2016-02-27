## Module Administration

The ModuleAdmin class made it easier to achieve a more uniform user experience in XOOPS administration.
The standard features it made available gave us friendlier administration features with less code.
The only problem is it has been a bit of a moving target. In the next generation, the Frameworks code
disappears and Xoops\Module\Admin move the functions to core. This move also adds several improvements,
but some of the 2.5.x calls are incompatible with the new version.

With XMF you can make your module's administration area code forward compatible by using the
[Xmf\Module\Admin](../module/admin.md) class.

* [Hide and Seek with Icons](modadm-icons.md)
    * Where are the icons?
    * menu.php icons
* [Standard Admin Pages](modadm-pages.md)
    * index.php conversion
    * pages.php conversion


