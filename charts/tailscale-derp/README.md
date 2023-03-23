# tailscale-derp Helm Chart

This Helm Chart is a Tailscale container deployment for a tailnet relay server (DERP).

## Installing the Helm Chart

```shell
helm repo add tailscale https://spreitzer.ch/helm-tailscale
helm install tailscale-derp tailscale/tailscale-derp
```

## Helm Chart Configuration Examples

A working configuration:

```yaml
service:
  annotations:
    service.beta.kubernetes.io/azure-dns-label-name: my-derp-01

hostname: my-derp-01.switzerlandnorth.cloudapp.azure.com

nodeSelector:
  topology.kubernetes.io/region: switzerlandnorth
  topology.kubernetes.io/zone: switzerlandnorth-1
```

## Helm Chart Values

| Key | Description | Default |
|---|---|---|
| `image.name` | Name of the container image to use. | `docker.io/sspreitzer/tailscale-derp` |
| `image.pullPolicy` | Kubernetes pullPolicy to use for starting the container image. | `IfNotPresent` |
| `service.type` | Kubernetes Service type. | `LoadBalancer` |
| `service.annotations` | A map/dict of Kubernetes Service annotations. | `{}` |
| `hostname` | DERP hostname to use. Must be the same as of the derpMap in the tailnet ACL. | `derp.example.com` |
| `nodeSelector` | A map/dict of Kubernetes Pod nodeSelector node labels. | `{}` |
| `affinity` | A map/dict of Kubernetes Pod affinity rules. | `{}` |
