# wise-prometheus-demo

A demo monitoring solution with [Prometheus](https://prometheus.io/), [Grafana](http://grafana.org/), [cAdvisor](https://github.com/google/cadvisor),
[NodeExporter](https://github.com/prometheus/node_exporter) and alerting with [AlertManager](https://github.com/prometheus/alertmanager).

## Install

Clone this repository on your Prometheus host and run compose up:

```bash
git clone https://github.com/m1g0r/wise-prometheus-demo
cd wise-prometheus-demo
docker-compose up -d
```
For start WordPress demo site with [cAdvisor](https://github.com/google/cadvisor) and [NodeExporter](https://github.com/prometheus/node_exporter) your should clone this repository on wordpress host and run compose up:

```bash
git clone https://github.com/m1g0r/wise-prometheus-demo
cd wise-prometheus-demo/wordpress
docker-compose up -d
```

Prerequisites:

* Docker Engine
* Docker Compose

Containers:

* Prometheus (metrics database) `http://<host-ip>:9090`
* AlertManager (alerts management) `http://<host-ip>:9093`
* Grafana (visualize metrics) `http://<host-ip>`
* NodeExporter (host metrics collector) `http://<host-ip>:9100`
* cAdvisor (containers metrics collector) `http://<host-ip>:8080`

## Setup Grafana

Navigate to `http://<host-ip>` and login with user ***admin*** password ***admin***.

## Setup alerting

The AlertManager service is responsible for handling alerts sent by Prometheus server.
AlertManager can send notifications via email, Pushover, Slack, HipChat or any other system that exposes a webhook interface.
A complete list of integrations can be found [here](https://prometheus.io/docs/alerting/configuration).

You can view and silence notifications by accessing `http://<host-ip>:9093`.

To receive alerts via Slack you need to make a custom integration by choose ***incoming web hooks*** in your Slack team app page.
You can find more details on setting up Slack integration [here](http://www.robustperception.io/using-slack-with-the-alertmanager/).
