libdnet
-------

This is a fork of https://github.com/ofalk/libdnet to address an open issue with addr_pton().
It removes the gethostbyname() usage, to keep resolver code out of addr_pton().  Hence addr_pton()
will always return a consistent error if the first argument isn't an address string.
