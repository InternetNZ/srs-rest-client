SRS REST API CLIENT (RAC)
=========================

This is a simple command line interface to query the SRS REST API for
domain name availability and the list of soon to be release domain names
(droplist).

Output can either be in human readable text or as JSON.

REQUIREMENTS
------------

`rac` uses the following non-standard python modules: requests.

These are all available as Debian packages, to install them run:
`sudo apt-get install python3-requests`.

ENVIRONMENT
-----------

The following environment variables can be used:

* `REST_SERVER` The hostname of the server running the REST API, used when
  `--server` is not specified.

* `REST_CERTIFICATE` SSL CA certificate that authenticates the HTTPS
  connection, used when `--certificate` is not specified.

KEYS
----

The following keys are in the `registry/` directory:

* `srs-root-ca.pem` The SSL CA certificate used to authenticate the SSL
  connection.

USAGE
-----

Usage: `rac ACTION OPTIONS`. Run `rac help` to see available
actions.

Each action has a help message that shows all the possible options for that
action and brief, what they do. Run `rac help ACTION` to see that help, eg:

```sh
rac help availability
```

All requests require the following to be specified:

* The REST API server  name specified using `--server`.

In the following examples, each option is shown on it's own line for readability,
your shell will require everything to be on one line.

The `availability` command is used to get a the status of one or more domain names.

It takes either a list of domains or a prefix to check against all available second
level domains.

```sh
rac availability
  --server avail.test.srs.net.nz
  --domain example.co.nz
```

To search against all available second level domains use `--search`.

```sh
rac availability
  --server avail.test.srs.net.nz
  --search example
```

Fetch the list of soon to be released domain names.

```sh
rac droplist
  --server avail.test.srs.net.nz
```
