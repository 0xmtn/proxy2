# proxy2

HTTP/HTTPS proxy in a single python script


## Features

* easy to customize
* require no external modules
* support both of IPv4 and IPv6
* support HTTP/1.1 Persistent Connection
* support dynamic certificate generation for HTTPS intercept

This script works on Python 2.7.
You need to install OpenSSL to use as a HTTPS proxy.


## Usage

Just run as a script:

```
$ python proxy2.py
```

Above command runs the proxy on tcp/8080.
To use another port, specify the port number as the first argument.

```
$ python proxy2.py 10443
```

Through the proxy, you can access http://proxy2.test/ and install the CA certificate for HTTPS intercept.


## Customization

You can easily customize the proxy and rewrite the requests/responses or save something to the files.
The ProxyRequestHandler class has 3 methods to customize:

* request_handler: called before accessing the upstream server
* response_handler: called before responding to the client
* save_handler: called after responding to the client with the exclusive lock, so you can safely write out to the terminal or the file system

By default, only save_handler is implemented which outputs the HTTP(S) headers and some of the request body to the standard output.
