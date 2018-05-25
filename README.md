# nagiosapi

[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://opensource.org/licenses/MIT)
[![circleci](https://circleci.com/gh/rmcintosh/nagiosapi.svg?style=shield&circle-token=:circle-token)](https://circleci.com/gh/rmcintosh/nagiosapi)

## Requirements

- A running Nagios instance.
- Docker (Optional)

## Installation

```sh
$ git clone git@github.com:rmcintosh/nagiosapi.git
$ cd nagiosapi/
```

From there you can choose to run it as a standard python application, or with Docker.

### Standard

```sh
$ pip install -r requirements.txt
$ cd nagiosapi/
$ export NAGIOS_STATUS_PATH=/usr/local/nagios/var/status.dat
$ uwsgi --http :9090 --wsgi nagiosapi:app --master
```

### Docker

```sh
$ docker build -t rmcintosh/nagiosapi .
$ docker run -d \
    --name nagiosapi
    -p 9090:9090 \
    -e NAGIOS_STATUS_PATH=/usr/local/nagios/var/status.dat \
    -v /usr/local/nagios/var/:/usr/local/nagios/var/:ro
    rmcintosh/nagiosapi
```

### Notes

Currently, all endpoints are GET/read-only.
