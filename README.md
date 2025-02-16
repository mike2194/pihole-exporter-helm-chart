# Pihole Exporter Helm Chart

TL;DR;

```
helm repo add pihole https://github.com/mike2194/pihole-exporter-helm-chart/raw/master/charts
helm install -name pihole-exporter --namespace pihole pihole/pihole-exporter
```

Using an auth token:
```
helm install \
  -name pihole-exporter \
  --namespace pihole \
  --set secretEnvVars.PIHOLE_APITOKEN=myPiHoleApiToken \
  pihole/pihole-exporter
```

Using a password:
```
helm install \
  -name pihole-exporter \
  --namespace pihole \
  --set secretEnvVars.PIHOLE_PASSWORD=myPiHolePassword \
  pihole/pihole-exporter
```

Setting the hostname with a password:
```
helm install \
  -name pihole-exporter \
  --namespace pihole \
  --set secretEnvVars.PIHOLE_PASSWORD=myPiHolePassword \
  --set extraEnvVars.PIHOLE_HOSTNAME=my.pihole.server \
  pihole/pihole-exporter
```

## Introduction

This chart deploys the pihole-exporter by eko - https://github.com/eko/pihole-exporter to a kubernetes cluster.

## Notes
I have not set a default configuration, please modify the values.yaml file with your correct config settings.

## Configuration

| Parameter                     | Description                           | Default |
| :---------------------------- | :------------------------------------ | ------: |
| service.port                  | Port for the kubernetes service       |    9617 |
| extraEnvVars.INTERVAL         | How often to poll pihole stats        |     10s |
| extraEnvVars.PIHOLE_HOSTNAME  | Pihole Hostname                       |    None |
| secretEnvVars.PIHOLE_PASSWORD | Pihole admin user password            |    None |
| secretEnvVars.PIHOLE_APITOKEN | Pihole api token                      |    None |
| extraEnvVars.PORT             | Change default webserver port for app |    9617 |
