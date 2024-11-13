# Kepimetheus Helm Charts

[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/promql-translator)](https://artifacthub.io/packages/helm/kepimetheus/promql-translator)
[![License](https://img.shields.io/github/license/kepimetheus/helm-charts)](https://github.com/kepimetheus/helm-charts/blob/main/LICENSE)
[![Release](https://img.shields.io/github/v/release/kepimetheus/helm-charts)](https://github.com/kepimetheus/helm-charts/releases)

This Helm chart deploys an application that translates natural language queries into PromQL (Prometheus Query Language) using AWS Bedrock.

## Usage

[Helm](https://helm.sh) must be installed to use the charts.
Please refer to Helm's [documentation](https://helm.sh/docs/) to get started.

Once Helm is set up properly, add the repository as follows:

```shell
helm repo add kepimetheus https://define-helm-repository
```

You can then run `helm search repo kepimetheus` to see the charts.

## Contributing

The source code of all [Kepimetheus](https://kepimetheus.github.io/epimetheus.github.io/) community [Helm](https://helm.sh) charts can be found on Github: <https://github.com/kepimetheus/helm-charts>