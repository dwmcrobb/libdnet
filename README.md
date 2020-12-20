libdnet
-------

This is a fork of https://github.com/ofalk/libdnet to address an open issue with addr_pton().
It removes the gethostbyname() usage, to keep resolver code out of addr_pton().  Hence addr_pton()
will always return a consistent error if the first argument isn't an address string.

I also introduced INTF_FLAG_RUNNING for interface flags.  This helps address the fact that
INTF_FLAG_UP on Linux doesn't represent the operational state.  A caller can now check the
INTF_FLAG_RUNNING bit to get a bettter picture of operational status.  To be more consisitent
across BSD, Linux and Windows, I also modified intf-win32.c to set INTF_FLAG_UP based on 
dwmAdminStatus alone, and set INTF_FLAG_RUNNING if dwOperStatus is MIB_IF_OPER_STATUS_OPERATIONAL
or MIB_IF_OPER_STATUS_CONNECTED.
