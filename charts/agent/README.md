# agent

![Version: 0.2.8](https://img.shields.io/badge/Version-0.2.8-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: v0.25.0](https://img.shields.io/badge/AppVersion-v0.25.0-informational?style=flat-square)

A Helm chart for Grafana Agent

## Source Code

* <https://github.com/grafana/agent>

## Chart Repo

```shell
helm repo add grafana https://grafana.github.io/helm-charts
```

_See [helm repo](https://helm.sh/docs/helm/helm_repo/) for command documentation._

## Deploy Grafana Agent

This kind of deployment uses configuration specified at the time of deployment.

```shell
cat <<END | helm upgrade --create-namespace --namespace grafana --values - --install agent grafana/agent
# Keep the resource names simple
fullnameOverride: grafana-agent
# Run 3 replicas of the agent
prometheus:
  replicas: 3
END
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | Pod affinity |
| annotations | object | `{}` | GrafanaAgent annotations |
| extras | object | `{}` | Extra GrafanaAgent configuration |
| image.pullSecrets | list | `[]` | List of image pull secrets |
| image.repository | string | `"grafana/agent"` | Image repository and name |
| image.tag | string | `""` | Overrides the image tag whose default is the chart `appVersion` |
| logLevel | string | `"info"` | Log level |
| logs.create | bool | `true` | Whether to configure logs Agent. |
| logs.extras | object | `{}` | Extra settings for logs-specific pods |
| logs.instanceSelectorMatchExpressions | list | `[]` | LogsInstance selector based on expression matching |
| logs.instanceSelectorMatchLabels | object | `{"agent":"grafana-agent"}` | LogsInstance selector based on label matching |
| metrics.create | bool | `true` | Whether to configure metrics Agent. |
| metrics.extras | object | `{}` | Extra settings for metrics-specific pods |
| metrics.instanceSelectorMatchExpressions | list | `[]` | PrometheusInstance selector based on expression matching |
| metrics.instanceSelectorMatchLabels | object | `{"agent":"grafana-agent"}` | PrometheusInstance selector based on label matching |
| metrics.replicas | int | `1` | Number of replicas of each shard to deploy for metrics pods |
| nodeSelector | object | `{}` | Pod node selector |
| podAnnotations | object | `{}` | Pod annotations |
| rbac.create | bool | `true` | Whether to create Cluster Role and Cluster Role Binding |
| rbac.extraClusterRoleRules | list | `[]` | Extra ClusterRole rules |
| rbac.useExistingRole | string | `nil` | Use an existing ClusterRole/Role |
| resources | object | `{}` | Resources for the Agent container |
| securityContext | object | `{}` | Security context for the Agent container |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Whether to create the Service Account used by the Pod |
| serviceAccount.name | string | `""` | If not set and `create` is `true`, a name is generated using the fullname template |
| tolerations | list | `[]` | Pod tolerations |
| volumeMounts | list | `[]` | Volume mounts for GrafanaAgent |
| volumes | list | `[]` | Volumes for GrafanaAgent |

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| Jiri Tyr | <jiri.tyr@gmail.com> | <https://github.com/jtyr> |