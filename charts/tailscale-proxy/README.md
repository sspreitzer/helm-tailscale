# tailscale-proxy Helm Chart

This Helm Chart is a Tailscale container deployment to handle tailnet requests to a destination IP.

## Installing the Helm Chart

```shell
helm repo add tailscale https://spreitzer.ch/helm-tailscale
helm install tailscale-proxy tailscale/tailscale-proxy
```

## Helm Chart Configuration Examples

A working configuration:

```yaml
auth:
  key: tskey-xxxxxx

destination:
  # Eg. In-cluster Kubernetes api
  ip: 10.0.0.1

hostname: k8s-mycluster-api

dns: 
  searches:
    - tail12345.ts.net

tags:
  - 'tag:kubernetes-api'
```

Disabling IPv6:

```yaml
sysctl:
  net.ipv4.ip_forward: 1
  net.ipv6.conf.all.disable_ipv6: 1
  net.ipv6.conf.all.forwarding: 0
```

## Helm Chart Values

| Key | Description | Default |
|---|---|---|
| `auth.existingSecret` | If set uses an exising Kubernetes Secret instead. | `''` |
| `auth.key` | Tailnet authentication key. | `tskey-0123456789abcdef` |
| `destination.ip` | IP to forward incoming tailnet traffic to. | `10.0.0.1` |
| `sysctl` | A map/dict of sysctl settings to configure before starting the tailnet daemon. | [See values.yaml](./values.yaml) |
| `hostname` | The name of the tailnet node. | `kubernetes-tailnet-proxy` |
| `dns.nameservers` | An array/list of additional DNS nameservers for the proxy container. | `['100.100.100.100']` |
| `dns.searches` | An array/list of additional DNS search domain suffixes for the proxy container. | `['tailxxxxx.ts.net']` |
| `image.name` | Name of the container image to use. | `ghcr.io/tailscale/tailscale` |
| `image.pullPolicy` | Kubernetes pullPolicy to use for starting the container image. | `IfNotPresent` |
| `tags` | An array/list of tailnet tags to use for this node. | `[]` |
