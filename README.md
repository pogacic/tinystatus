# Tinystatus

tinystatus generate an html status page via shell script.

Verified working on `Ubuntu 24.04 LTS`.

## Requirements
- Netcat (`sudo apt install netcat-traditional`)
- curl (`sudo apt install curl`)
- ping
- systemctl

## Features

* Parallel checks
* HTTP, ping, port checks
* HTTP expected status code (401, ...)
* Minimal dependencies (curl, nc and coreutils)
* Easy configuration and customisation
* Tiny (~1kb) optimized result page
* Incident history (manual)
* Check if system service is operating normally (FORK ADDITION)
* Check if process exists (FORK ADDITION)

## Demo

An example site is available [here](https://lab.bdro.fr/tinystatus/).

## Setup

To install tinystatus:

* Clone the repository and go to the created directory
* Edit the checks file `checks.csv`
* To add incidents or maintenance, edit `incidents.txt`
* Generate status page `./tinystatus > index.html`
* Serve the page with your favorite web server

## Configuration file

The syntax of `checks.csv` file is:
```
Command, Expected Code, Status Text, Host to check
```

Command can be:
* `http` - Check http status
* `ping` - Check ping status 
* `port` - Check open port status
* `service` - Check a service is running with systemctl
* `proc-cmd` - Check if a process is running via command value

There are also `http4`, `http6`, `ping4`, `ping6`, `port4`, `port6` for IPv4 or IPv6 only check.  
Note: `port4` and `port6` require OpenBSD `nc` binary.

