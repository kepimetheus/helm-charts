# kepimetheus

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.0.1](https://img.shields.io/badge/AppVersion-0.0.1-informational?style=flat-square)

A Helm chart for kepimetheus on Kubernetes

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Rodrigo Melgar | <rodrigomelgar@gmail.com> |  |
| Felipe Barbosa | <lybrbarbosa@gmail.com> |  |
| Romulo Scampini | <romulo@scampini.com.br> |  |

## Source Code

* <https://github.com/randomk/kepimetheus>

## Installing the Chart

Before you can install the chart you will need to add the `kepimetheus` repo to [Helm](https://helm.sh/).

```shell
helm repo add kepimetheus https://define-helm-repository
```

After you've installed the repo you can install the chart.

```shell
helm upgrade --install kepimetheus kepimetheus/kepimetheus --version 0.0.1
```

## Providers

For set up for a specific provider using the Helm chart, see the following links:

- [AWS Bedrock]()

## Requirements

Kubernetes: `>=1.20.0-0`

| Repository | Name | Version |
|------------|------|---------|
| https://prometheus-community.github.io/helm-charts | kube-prometheus-stack | 65.2.* |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Assign custom affinity rules to the alertmanager instance ref: https://kubernetes.io/docs/concepts/configuration/assign-pod-node/ |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` | Image pull policy for the `kepimetheus` container. |
| image.repository | string | `"rodrigomelgar/kepimetheus"` | Image repository for the `kepimetheus` container. |
| image.tag | string | `""` | Image tag for the `kepimetheus` container, this will default to `.Chart.AppVersion` if not set. |
| imagePullSecrets | list | `[]` |  |
| ingress.annotations | object | `{}` |  |
| ingress.className | string | `""` |  |
| ingress.enabled | bool | `false` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"` |  |
| ingress.tls | list | `[]` |  |
| kubePrometheusStack | object | `{"enabled":false}` | Install kube prometheus stack using default values from https://github.com/prometheus-community/helm-charts/blob/main/charts/kube-prometheus-stack/values.yaml |
| livenessProbe.httpGet.path | string | `"/"` |  |
| livenessProbe.httpGet.port | string | `"http"` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` | Define which Nodes the Pods are scheduled on. ref: https://kubernetes.io/docs/user-guide/node-selection/ |
| podAnnotations | object | `{}` |  |
| podLabels | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| provider.name | string | `"awsBedrock"` |  |
| provider.secret.annotations | object | `{}` | Annotations to add to the secret. |
| provider.secret.create | bool | `true` | If `true`, create a new `Secret` for provider access. |
| provider.secret.labels | object | `{}` | Labels to add to the secret. |
| provider.secret.name | string | `nil` | Name to add to the secret. |
| provider.secret.stringData | object | `{"AWS_ACCESS_KEY_ID":null,"AWS_SECRET_ACCESS_KEY":null}` | String data to add to the secret. |
| readinessProbe.httpGet.path | string | `"/"` |  |
| readinessProbe.httpGet.port | string | `"http"` |  |
| replicaCount | int | `1` | The number of pod `replicas` to deploy. |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `8000` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account. |
| serviceAccount.automountServiceAccountToken | string | `nil` | Set this to `false` to [opt out of API credential automounting](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/#opt-out-of-api-credential-automounting) for the `ServiceAccount`. |
| serviceAccount.create | bool | `true` | If `true`, create a new `ServiceAccount`. |
| serviceAccount.labels | object | `{}` | Labels to add to the service account. |
| serviceAccount.name | string | `nil` | If this is set and `serviceAccount.create` is `true` this will be used for the created `ServiceAccount` name, if set and `serviceAccount.create` is `false` then this will define an existing `ServiceAccount` to use. |
| tolerations | list | `[]` | If specified, the pod's tolerations. ref: https://kubernetes.io/docs/concepts/configuration/taint-and-toleration/ |
| volumeMounts | list | `[]` | Additional volumeMounts on the output Deployment definition. |
| volumes | list | `[]` | Additional volumes on the output Deployment definition. |

----------------------------------------------

Autogenerated from chart metadata using [helm-docs](https://github.com/norwoodj/helm-docs/).