# helm-tailscale
A collection of Helm charts for the Tailscale VPN mesh

## Helm Charts Documentation

* [tailscale-proxy](charts/tailscale-proxy/)
* [tailscale-derp](charts/tailscale-derp/)

## Add the Helm Repository

```shell
helm repo add tailscale https://spreitzer.ch/helm-tailscale
```

## Install a Tailscale Helm Chart

```shell
helm install tailscale-derp tailscale/tailscale-derp
```
