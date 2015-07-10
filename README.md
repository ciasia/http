Netlinx HTTP lib
====
A minimal HTTP library for working with web services natively in NetLinx.


Usage
-----

As there’s no blocking socket IO in NetLinx when you make a call to any of the request function (`http_get`, `http_head`, `http_put`, `http_post`, `http_patch` or `http_delete`) this will return you a unique ‘sequence number’.

When a response is received it will call back to a function `http_response_received(..)` which you implement in your code. This will contain 3 arguments: the sequence number, the full request object and a fully parsed response object ready for you to deal with as you like. If you’re not interested in response feel free to omit this, otherwise just pop in a `#define HTTP_RESPONSE_CALLBACK` - similar to the RMS SDK.

An error, when encountered, will callback to `http_error(..)` along with the sequence number, the target request host, the full request object and an error number. `#define HTTP_ERROR_CALLBACK` signifies you’re interested in dealing with these.

By default it can handle up to 10 parallel requests but if you’re really hammering it, or dealing with a slow connection / server this can be bumped up or down by changing `HTTP_MAX_PARALLEL_REQUESTS`.


Other info
----------

This software is distributed under [MIT license](http://www.opensource.org/licenses/mit-license.php), so feel free to integrate it in your commercial products.