# shinken-pack-collectd-carbon-cache

## Description

This Shinken monitoring pack is used to manage carbon-cache services with our
standard deployment of Collectd.

We request Collectd data using unixsock plugin and collectd-nagios script from
collecd-utils package.

This pack depends to shinken-pack-collectd-base to work

## Objects

### Templates

#### Host templates

* collectd-carbon-cache: Manage all default thresholds and values for services

### Services

| Service name                   | Description                  | Value specification                            | DS        | Consolidation | Warning variable | Critical variable | Duplicate_foreach variable |
|--------------------------------|------------------------------|------------------------------------------------|-----------|---------------|------------------|-------------------|----------------------------|
| carbon-cache - $KEY$ processes | Check carbon-cache processes | processes-$VALUE1$/ps_count                    | processes | none          | $VALUE2$         | $VALUE3$          | _carbon_cache_processes    |
| carbon-cache - $KEY$           | Check listening ports        | tcpconns-$VALUE1$-local/tcp_connections-LISTEN | value     | none          | $VALUE2$         | $VALUE3$          | _carbon_cache_listen       |

## Default values

    _carbon_cache_processes    carbon-cache $(carbon-cache)$$(1:)$$(1:)$
    _carbon_cache_listen       Listen 2003 $(2003)$$(1:1)$$(1:1)$
