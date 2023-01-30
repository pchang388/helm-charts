# simple-unifipoller
This is repository contains a helm chart that can be used to deploy unpoller (Unifi Controller metrics collector) in a simple manner without being coupled to a controller deploy and while also providing helpful comments and tips from my personal experiences.

## Dependencies
* Helm v3.X (tested on v3.11.0)
* Kubernetes v1.2X (tested on v1.25.6)

## Why another chart? There's already a few out there
* I wanted something that was minimal and did not package a unifi controller deploy in the helm chart
  * Reduce bloat/text in values file and also less things to maintain and update
  * Personally, I want to avoid putting the unifi controller in a kubernetes pod especially for a homelab where things can break often and don't want my controller being offline during those times
    * I opted to put the unifi controller on its own lxc container and run separate from my k8 cluster. Run it with docker-compose now for simplicity and uptime
  * I also ran into some small issues while setting it up and wanted to share my findings, hopefully they help someone
