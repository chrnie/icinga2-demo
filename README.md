# icinga2-demo
demo config with fully simulated hosts and services

## Introduction

This demo simulates hosts and services with in a whole environment. All host and service checks are based on the dummy check_command but are extended with a little bit more magic.
It calculates the exit value of each check by the following aspects:

## icinga2

### Install

- copy icinga2-demo.d to /etc/icinga2.conf
- add to /etc/icinga2/icinga2.conf
```
include_recursive "icinga2-demo.d"
```
- if not using the example configuration provided by the icinga2 project be sure to keep or move your api-users


### Simulated Environment

Hosts:
- is the core router reachable?
- is one of the switches reachable?
  - this contains full path checking, from the icinga2 server's point of view.
- is this host in a special offline period?

Services:
- is the parent host online?
- is there a dependency of another service
  - for example a database service depends on it's mounted storage and the storage cannot be mounted if the storage service running on the storage cluster is offline
- is this service in a special offline period?

The scenario contains dependencies, notification rules, users and groups of all kinds.

![Datacenter Structure](doc/images/icinga-report_icinga2-testcase_serviceview.png "Datacenter Structure")
![Service Structure](doc/images/icinga-report_icinga2-testcase.png "Service Structure")


## Nagvis & Business Process
