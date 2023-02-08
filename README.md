# Helm charts
## simple-unifipoller
### Easy Prometheus Metrics for Unifi Controllers
This is repository contains a helm chart that can be used to deploy unpoller (Unifi Controller metrics collector)  for *_prometheus_* metrics in a simple manner without being coupled to a controller deploy and while also providing helpful comments.

Link here to chart with more details for Github page users: https://github.com/pchang388/simple-unifipoller/tree/main/helm

### Applications Used
* Unifi Controller
    - https://hub.docker.com/r/linuxserver/unifi-controller
* Unpoller
    - https://github.com/unpoller/unpoller
* Prometheus + Grafana

### Dependencies
* Helm `v3.X` (tested on `v3.11.0`)
* Kubernetes `v1.2X` (tested on `v1.25.6`)

### Why another chart? There's already a few out there
1. I wanted something that was minimal that did not package a unifi controller deploy in the helm chart
2. I already have a controller deployed somewhere else and more isolated. But I also have all my metrics in promtheus in my existing k8 cluster and want to manage it there.
3. Reduce bloat/text in values file and also less things to maintain and update
4. Personally, I want to avoid putting the unifi controller in a kubernetes pod especially for a homelab where things can break often and don't want my controller being offline during those times
 - I opted to put the unifi controller on its own lxc container and run separate from my k8 cluster. Run it with docker-compose now for simplicity and uptime
5. I also ran into some small issues while setting it up and wanted to share my findings, hopefully they help someone
