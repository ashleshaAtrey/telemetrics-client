telemetrics.conf(5) -- Telemetry service configuration file
===========================================================

## SYNOPSIS

```
/etc/telemetrics/telemetrics.conf
/usr/share/defaults/telemetrics/telemetrics.conf
```

## DESCRIPTION

This file contains configuration parameters for the `telemd(1)` telemetry
service daemon. The daemon reads this file at startup if it exists.

## SYNTAX

The configuration file contains `key=value` pairs, formatted as plain
text, one option per line. Comments can be added by preceding them with the
`#` character. All configuration options should be in a section marked
with `[settings]`.

## OPTIONS

 * `server`=<url>:
   Server URL including protocol designator.

 * `socket_path`=<path>:
   Path to the socket that `telemd` will listen on.

 * `cainfo`=<path>:
  Certificate file to use for validation of SSL endpoint.

 * `tidheader`=<header>:
  Telemetry ID in header format, usually
    `tidheader=X-Telemetry-TID:<uuid>`
  post header used to group records in ingestion service, which may be
  ingesting for more than one set of clients. Can be set to any string.

 * `record_expiry`=<minutes>:
  Record expiry time in minutes.

 * `spool_dir`=<`dir`>:
  Local spool directory used to store records being processed.

 * `spool_max_size`=<kB>:
  maximum size of the spool directory in kB. A value of `-1` indicates
  no limit. The block size of the files in this directory is considered,
  and not the actual size of the record itself.

 * `spool_process_time`=<seconds>:
  Time in seconds for processing spool. Valid range: 120..3600. Values
  outside this range are clamped.

 * `rate_limit_enabled`=<`true`|`false`>:
  Enable rate limiting. If this is set to false then all rate-limiting
  disabled. It is possible to disable each rate-limit individually below.

 * `record_burst_limit`=<limit>:
  Rate limiting record burst limit. Valid Range:  0..`INT_MAX`, -1 = disabled.

 * `record_window_length`=<minutes>:
  Rate limiting record window length in minutes. Valid Range: 0..59.

 * `byte_burst_limit`=<limit>:
  Rate limiting byte burst limit. Valid Range:  0..`INT_MAX`, -1 = disabled.

 * `byte_window_length`=<minutes>:
  Rate limiting byte window length in minutes. Valid Range: 0..59.

 * `rate_limit_strategy`=<strategy>:
  Rate limit strategy - what to do with record if rate-limiting prevents
  delivery over network. Valid stategies: `spool`, `drop`.


## COPYRIGHT

 * Copyright (C) 2016 Intel Corporation, License: CC-BY-SA-3.0

## SEE ALSO

`telemd(1)`

https://github.com/clearlinux/telemetrics-client

https://clearlinux.org/documentation/

## NOTES

Creative Commons Attribution-ShareAlike 3.0 Unported

 * http://creativecommons.org/licenses/by-sa/3.0/