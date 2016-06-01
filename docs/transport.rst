Transport options
=================
If you need to change options like cache, timeout or ssl verification
use `Transport` class.

For instance to disable SSL verification use `verify` option::

    >>> from zeep import Client
    >>> from zeep.transports import Transport
    >>> transport = Transport(verify=False)
    >>> client = Client(
    ...     'http://www.webservicex.net/ConvertSpeed.asmx?WSDL',
    ...     transport=transport)


Caching
-------
The default cache backed is SqliteCache.  It caches the WSDL and XSD files for 
1 hour by default. You can disable caching by passing `None` as value to the
`Transport.cache` attribute when initializing the client::

    >>> from zeep import Client
    >>> from zeep.cache import SqliteCache
    >>> from zeep.transports import Transport
    >>> transport = Transport(cache=None)
    >>> client = Client(
    ...     'http://www.webservicex.net/ConvertSpeed.asmx?WSDL', 
    ...     transport=transport)


Changing the SqliteCache settings can be done via::


    >>> from zeep import Client
    >>> from zeep.cache import SqliteCache
    >>> from zeep.transports import Transport
    >>> cache = SqliteCache(persistent=True, timeout=60)
    >>> transport = Transport(cache=cache)
    >>> client = Client(
    ...     'http://www.webservicex.net/ConvertSpeed.asmx?WSDL',
    ...     transport=transport)

