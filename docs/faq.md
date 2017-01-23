# FAQ

Frequently Asked Questions when working with Cloud4Rpi

## Insecure Platform Warning

Error `"InsecurePlatformWarning: A true SSLContext object is not available..."`

You need Python version 2.7.9 or higher installed. Please check it with

``` bash
$ python --version
```

and update if necessary.

``` bash
$ wget https://www.python.org/ftp/python/2.7.9/Python-2.7.9.tgz
$ gunzip Python-2.7.9.tgz
$ tar -xvf Python-2.7.9.tar
$ cd Python-2.7.9/
$ ./configure
$ make
$ sudo make install
```

## Where can I find .log file for service?

If you use ```.../examples/raspberrypi/control.py``` as a service the default path for log-file is *'/var/log/cloud4rpi.log'*

But you can specify your log file location via LOG_FILE_PATH variable:

```LOG_FILE_PATH = '/var/log/cloud4rpi.log'```


The following code is required to activate logging to file:

```cloud4rpi.set_logging_to_file(LOG_FILE_PATH)```