# About

`RHMAP Monitoring` uses `InfluxDB` and `Grafana` to generate graphs of system statistics for `RHMAP` cloud apps / services. It is a `Docker` based solution which could be deployed to any containerised infrastructure.
`InfluxDB` is a time series based Database which accepts data through a UDP port and `Grafana` is data visualisation tool which draws pretty graphs with time based queries.

## Docker Component

Following docker components will be included:

* nginx
* influxdb
* grafana


# Pre-requests

## Server Requirement

* 2 GB memory
* 2 cores
* 30 GB Disk Space -- according to retention policy
* Docker > 1.11.0
* Firewall (see below)

## Configuration

* `docker-compose.yml`: Config containers like data storage (volume) / log size / ports / quota etc
* `nginx/default.conf`: Config domain name (see below) / use of https (if needed) / simple auth etc
* `influxdb/config.toml`: Config influxdb see details [here](https://docs.influxdata.com/influxdb/v1.2/administration/config/)

It is able to use the stack without any modification.

## Firewall Config

Following ports should be accessible (with default config):

* 80: For portal http access 
* 2003/UDP: For RHMAP cloud app sending statistic data to influxdb

## Data storage

By default, data will be stored in `/rhmap` folder. This can be changed in `docker-compose.yml` file.

## Domain name

By default, bounded domain names are:

* `grafana.rhmapdev.me`: Grafana portal
* `influxdb.rhmapdev.me`: Influxdb query web portal
* `influxdb-api.rhmapdev.me`: Influxdb rest api endpoints (used by influxdb web portal)

It is able to change them in `nginx/default.conf` to any domain names. Just remind that, if there is no 
DNS resolve for those domain names, they should be added to `/etc/hosts` file accordingly.

# Installation

## Install containers

Installation of containers is very straight forward:

1. Upload whole folder to server
2. SSH into server and switch to user who could access `Docker` by typing `docker ps`
3. run `docker-compose up -d` at the root of the folder

This should tell Docker to pull images and start running. Once finished, run `docker ps` to see all services running ok.

## Install `rhmap-stats` to cloud apps

For any cloud apps that needs to be monitored, they should install `rhmap-stats` node.js module. Follow the instruction [here](https://github.com/redhat-mobile-consulting/rhmap-stats) for more details.



# Setup

After installation, there are some configurations needed.

## Grafana

### data store

See below example: 

![https://drive.google.com/uc?export=download&id=0ByuKQDQ-pFtiLXRaREN2VTFBU0E](https://drive.google.com/uc?export=download&id=0ByuKQDQ-pFtiLXRaREN2VTFBU0E)



### dashboard

TBD

## InfluxDB

## Data retention

The default retention policy in influxdb is not enabled thus it is important to setup retention policy on database `grafana`. Otherewise db size will increase all the time. See [here](https://docs.influxdata.com/influxdb/v1.2/query_language/database_management/#modify-retention-policies-with-alter-retention-policy) for how to setup retention policy.

# LICENSE
MIT