## Shape (shp) Extension for HHVM (HipHop virtual machine)

This is a port from PECL shape extensioni for [HipHop PHP VM][fb-hphp], with
some fixes and enhancements, which is a wrapper library to
[libshape][libshape].

"The Shapefile C Library provides the ability to write simple C programs for
reading, writing and updating (to a limited extent) ESRI Shapefiles"

### Prerequisites

This extension requires `libshp` library installed. On Gentoo it is included
in `sci-libs/shapelib` ebuild.

### Building & Installation

Installation currently requires a copy of HHVM (version 2.3 or later) to be
built from source on the local machine (not installed from your distribution's
packages, even currently available Gentoo ebuilds will not work), instructions
on how to do this are available on the [HipHop Wiki][fb-wiki]. Once done, the
following command will build the extension.

~~~
$ export HPHP_HOME=/path/to/hhvm
$ cd /path/to/extension
$ ./build.sh
~~~

This will produce a `shp.so` file, the dynamically-loadable extension.

To enable the extension, you need to have the following section in your HHVM
config file:

~~~
DynamicExtensionPath = /path/to/hhvm/extensions
DynamicExtensions {
        * = shp.so
}
~~~

Where `/path/to/hhvm/extensions` is a folder containing all HipHop extensions,
and `shp.so` is in it. This will cause the extension to be loaded when the
virtual machine starts up.

### Differences from PECL

* Added function `shp_get_array_from_object` to convert SHP object properties
to PHP array.
* Function `shp_create_simple_object` will fail if not all arguments are
passed.

As always, bugs should be reported to the issue tracker and patches are very
welcome.

[libshape]:  http://shapelib.maptools.org/ "libshape"
[fb-hphp]: https://github.com/facebook/hhvm "HipHop PHP"
[fb-wiki]: https://github.com/facebook/hhvm/wiki "HipHop Wiki"

