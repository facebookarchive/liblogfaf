# liblogfaf
Making syslog() not block

liblogfaf (faf stands for fire-and-forget) is a dynamic library that is
designed to be LD_PRELOAD-ed while starting a process that uses openlog() &
syslog() functions to send syslog messages. It overrides logging functions to
make log messages sent as UDP datagrams instead of getting written to /dev/log
(which can block). This is useful for processes that call syslog() as part of
their main execution flow and can therefore be easily broken when /dev/log
buffer gets full, for example when the process that is expected to read from it
(usually system syslog daemon like rsyslog or syslog-ng) stops doing that.

Please note that liblogfaf should *not* be used in an environment where
reliable log message delivery is required.

## Requirements
liblogfaf currently only works on Linux as it relies on /proc/ filesystem to
determine process cmdline.

## Building and installing liblogfaf
* Ensure you have libtool, autoconf, and automake installed;
* run `autoreconf -i` to generate autoconf and automake files;
* run `./configure`. You can pass the '--enable-debug' option to build
  liblogfaf in debug mode;
* `make` will build everything;
* `make install` will install the library along with the `logfaf` script.

## Using liblogfaf
The library comes with a `logfaf` script that can be used to start any binary
with liblogfaf enabled. For example, if you run:

    echo test | logfaf logger

You should see logger sending syslog UDP messages to 127.0.0.1:514

## License
liblogfaf is BSD-licensed. We also provide an additional patent grant.
