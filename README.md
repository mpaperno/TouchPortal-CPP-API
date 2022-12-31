# Network Client for Touch Portal Plugin API

[![Made for Touch Portal](https://img.shields.io/static/v1?style=flat&labelColor=5884b3&color=black&label=made%20for&message=Touch%20Portal&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAOCAYAAAAfSC3RAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAetJREFUeNp0UruqWlEQXUePb1HERi18gShYWVqJYGeXgF+Qzh9IGh8QiOmECIYkpRY21pZWFnZaqWBhUG4KjWih4msys8FLbrhZMOfsx6w1e9beWjAYBOMtx0eOGBEZzuczrtcreAyTyQSz2QxN04j3f3J84vim8+cNR4s3rKfTSUQQi8UQjUYlGYvFAtPpVIQ0u90eZrGvnHLXuOKcB1GpkkqlUCqVEA6HsVqt4HA4EAgEMJvNUC6XMRwOwWTRfhIi3e93WK1W1Go1dbTBYIDj8YhOp4NIJIJGo4FEIoF8Po/JZAKLxQIIUSIUChGrEy9Sr9cjQTKZJJvNRtlsVs3r9Tq53W6Vb+Cy0rQyQtd1OJ1O9b/dbpCTyHoul1O9z+dzGI1Gla7jFUiyGBWPx9FsNpHJZNBqtdDtdlXfAv3vZLmCB6SiJIlJhUIB/X7/cS0viXI8n8+nrBcRIblcLlSrVez3e4jrD6LsK3O8Xi8Vi0ViJ4nVid2kB3a7HY3HY2q325ROp8nv94s5d0XkSsR90OFwoOVySaPRiF6DiHs8nmdXn+QInIxKpaJclWe4Xq9fxGazAQvDYBAKfssDeMeD7zITc1gR/4M8isvlIn2+F3N+cIjMB76j4Ha7fb7bf8H7v5j0hYef/wgwAKl+FUPYXaLjAAAAAElFTkSuQmCC)](https://www.touch-portal.com)
[![Qt](https://img.shields.io/static/v1?style=flat&labelColor=white&color=41CD52&label=&message=Qt%20v5%20%26%20v6&logo=qt)](https://qt.io)
![Supported Platforms](https://img.shields.io/badge/platforms-Windows%20|%20MacOS%20|%20Linux-AA7722)
[![GPLv3 License](https://img.shields.io/badge/license-GPLv3-blue.svg)](LICENSE.GPL.txt)
[![LGPLv3 License](https://img.shields.io/badge/license-LGPLv3-blue.svg)](LICENSE.LGPL.txt)
![Latest tagged version](https://img.shields.io/github/v/tag/mpaperno/TouchPortal-CPP-API)

**A simple TCP/IP network client for use in [Touch Portal](https://www.touch-portal.com) plugins which wish to utilize the `Qt` C++ library/framework.**

-------------
## Features
- Handles bi-directional network transfer and JSON encode/decode of _Touch Portal_ messages.
- Uses Qt signals to deliver messages from _Touch Portal_ and inform of connection status changes.
- Send messages to _Touch Portal_ using Qt slots and/or direct client method invocations.
- Optimized for maximum throughput, no unnecessary data processing is performed (eg. assumes plugin author validates their own data before sending).
- Includes some optional convenience methods for working with incoming action/connector data (eg. convert JSON array of objects to a `QMap` with the data IDs as keys).
- Asynchronous socket operations, fully reentrant methods, and can be run in a separate thread if needed (with queued signals/slots communication).
- Supports _Touch Portal_ plugin API up to v6 (latest released version). Will be updated for future versions as they are released.

-------------
## Requirements
- Depends on the `QtCore` and `QtNetwork` libraries/modules.
- Requires a Qt event loop to process data (uses asynchronous socket operations).
	- Typically this would be provided by `Q[Core|Gui]Application::exec()`, but could also be wrapped in a custom class with own event
		loop for use outside of Qt applications (for example).
- The client should work on any platform supported by `QtNetwork` library.

Tested with `Qt` versions `5.12.12`, `5.15.7`, `6.4.1` on Windows 10/11, MacOS (Big Sur and later), and Linux (Debian 9 (buster) / Ubuntu 18.04 (bionic)).

-------------
## Using
The client consists of a single class -- `TPClientQt`.  The simplest way to use it in a project is to just include the source code files directly in the plugin build.

It can also be built/used as a shared or static library. The included CMake project file can be used to build this. By default it builds a shared library (DLL),
but setting the `BUILD_SHARED_LIBS` variable to 'OFF/FALSE' will build the static version instead.

In either case, just `#include "TPClientQt.h"` somewhere in your plugin code and you're good to go.

-------------
## Documentation

API documentation generated from source comments is published at: https://mpaperno.github.io/TPClientQt/

-------------
## Example

A working plugin using this client can be found at https://github.com/mpaperno/DSEP4TP

I will add a simpler example to this repository ASAP.

-------------
## Credits

This project is written, tested, and documented by myself, Maxim (Max) Paperno.<br/>
https://github.com/mpaperno/

Documentation generated with [Doxygen](https://www.doxygen.nl/) and styled with the most excellent [Doxygen Awesome](https://jothepro.github.io/doxygen-awesome-css).

-------------
## Copyright, License, and Disclaimer

TPClientQt Project <br />
COPYRIGHT: Maxim Paperno; All Rights Reserved.

Dual licensed under the terms of either the GNU General Public License (**GPL**)
or the GNU Lesser General Public License (**LGPL**), as published by the Free Software
Foundation, either **version 3** of the Licenses, or (at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

Copies of the GNU GPL and LGPL are included with this project
and are available at <http://www.gnu.org/licenses/>.

Except as contained in this copyright notice, the names of the authors or
their institutions shall not be used in advertising or otherwise to
promote the sale, use, or other dealings in, any product using this
Software, or any derivative of this Software, without prior written
authorization from the authors.

This project may also use 3rd-party Open Source software under the terms
of their respective licenses. The copyright notice above does not apply
to any 3rd-party components used within.
