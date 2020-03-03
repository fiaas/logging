=============
FIAAS Logging
=============

This library configures logging according to the current FIAAS recomended format.

Usage::

    from fiaas_logging import init_logging

    init_logging(format="json")


This would configure your application to emit JSON formatted logs on STDOUT.

Available options (all are keyword arguments to `init_logging`):


====== =============== =================================================
Key    Possible values Meaning
====== =============== =================================================
format `json`/`plain`  Select either JSON logging, or plain text logging
debug  `True`/`False`  Enable debug logging
====== =============== =================================================

The plain format contains the fields timestamp, level name, message, logger name, and thread name.
In the json format, there are more fields, with more detail. The fields in the json output are:

============ =======================================================================
Name         Meaning
============ =======================================================================
@timestamp   Timestamp of message
@version     Version, legacy field to support ELK stack at FINN (to be removed?)
LocationInfo A structure describing the code location that logged this message
message      The actual log message
extras       A structure containing extra fields. Used for thread context
throwable    A formatted stacktrace if the log message is the result of an exception
============ =======================================================================
