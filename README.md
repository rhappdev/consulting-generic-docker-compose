<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [Purpose](#purpose)
- [How to achieve this goal](#how-to-achieve-this-goal)
- [Components](#components)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Purpose
The end goal of this repo is to have have the setup time and steps involved in setting up a CI suite for consulting projects as minimal as possible.

# How to achieve this goal
1. A Dockerfile per component with all configuration done already.
2. Using docker compose to tie all thses seperate Dockerfiles together

# Components
- Jenkins
- SonarQube
- Grafana
- InfluxDB