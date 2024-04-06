# 1. Monitoring system

Date: 2024-04-04

## Status

Accepted

## Context
Fish watch is a fast growing system with various services interacting with each other, it makes scaling essential. 
Proper and trustworthy monitoring is the basis for making any decision about infrastructure changes (i.e. scaling, extensibility etc), proper monitoring should support business decisions.
We'd like to use a system that helps us get the full picture of correlated business events, connected services and amount of consumed resources.

## Alternatives

#### DataDog

DataDog is a monitoring service for cloud-scale applications that allows for monitoring of servers, databases, tools, and services, through a SaaS-based platform.
DataDog platform allows to visualize metrics data on a dashboard, and provides alerting. Solution can be integrated with Amazon Web Services (AWS), Microsoft Azure, Google Cloud Platform, Red Hat OpenShift etc… Cost of DataDog as a monitoring solution is **$15 USD per host, per month**

#### Graphana

Grafana is an open source solution for running data analytics, pulling up metrics that make sense of the massive amount of data & to monitor your apps with the help of customizable dashboards. Grafana connects with every possible database such as Graphite, Prometheus, Influx DB, ElasticSearch, MySQL, PostgreSQL etc. Solution is free of charge.

#### ELK Stack

"ELK" is the acronym for three open source projects: Elasticsearch, Logstash, and Kibana. Elasticsearch is a search and analytics engine. It allows us to aggregate logs, search on it and visualize it. Because it is an open source project there are no financial costs associated with buying the stack.

#### Amazon CloudWatch

Amazon CloudWatch is AWS alerting tool for sending notifications based on the severity levels of the inspected matrix. Approximate cost is $0.30 USD for first 10,000 metrics.

## Decision

We decided to choose Prometheus + Grafana.
It is mainly because of the cost involved and ability of Prometheus to collect rich metrics and provides a powerful querying language.
Grafana on the other hand, transforms metrics into meaningful visualizations. Both are compatible with many, if not most, data source types.

## Consequences
We would have to appoint some time of a developer / administrator to take care of the monitoring.
