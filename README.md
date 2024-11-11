# PromQL Translator Helm Chart

[![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/promql-translator)](https://artifacthub.io/packages/helm/kepimetheus/promql-translator)
[![License](https://img.shields.io/github/license/kepimetheus/helm-charts)](https://github.com/kepimetheus/helm-charts/blob/main/LICENSE)
[![Release](https://img.shields.io/github/v/release/kepimetheus/helm-charts)](https://github.com/kepimetheus/helm-charts/releases)

This Helm chart deploys a Flask application that translates natural language queries into PromQL (Prometheus Query Language) using AWS Bedrock with Claude model.

## Description

The PromQL Translator is a web application that helps users generate Prometheus queries using natural language. It leverages AWS Bedrock's Claude model to translate user input into valid PromQL syntax, making it easier for users to query their Prometheus metrics without deep knowledge of PromQL.

## Prerequisites

- Kubernetes 1.16+
- Helm 3.0+
- AWS credentials with access to Bedrock service
- Prometheus instance (for executing the generated queries)

## Features

- Natural language to PromQL translation
- Query validation and automatic correction
- Web interface for easy interaction
- AWS Bedrock integration with Claude v2 model
- Prometheus compatibility checking

## Installing the Chart

1. Add the Helm repository:
```bash
helm repo add promql-translator https://github.com/kepimetheus/helm-charts
helm repo update
```

2. Install the chart with the release name `my-release`:
```bash
helm install my-release promql-translator/promql-translator
```

## Configuration

The following table lists the configurable parameters of the PromQL Translator chart and their default values.

| Parameter | Description | Default |
|-----------|-------------|---------|
| `replicaCount` | Number of replicas | `1` |
| `image.repository` | Image repository | `""` |
| `image.tag` | Image tag | `"latest"` |
| `image.pullPolicy` | Image pull policy | `"IfNotPresent"` |
| `service.type` | Kubernetes Service type | `"ClusterIP"` |
| `service.port` | Service port | `8000` |
| `ingress.enabled` | Enable ingress | `false` |
| `resources.limits.cpu` | CPU limit | `"500m"` |
| `resources.limits.memory` | Memory limit | `"512Mi"` |
| `resources.requests.cpu` | CPU request | `"250m"` |
| `resources.requests.memory` | Memory request | `"256Mi"` |
| `aws.region` | AWS Region | `"us-east-1"` |
| `aws.bedrock.enabled` | Enable AWS Bedrock | `true` |
| `aws.credentials.secretName` | AWS credentials secret name | `"aws-credentials"` |

## AWS Credentials

Create a Kubernetes secret with your AWS credentials:

```bash
kubectl create secret generic aws-credentials \
  --from-literal=AWS_ACCESS_KEY_ID=your_access_key \
  --from-literal=AWS_SECRET_ACCESS_KEY=your_secret_key
```

## Values File Example

```yaml
replicaCount: 2

image:
  repository: your-registry/promql-translator
  tag: v1.0.0
  pullPolicy: IfNotPresent

service:
  type: ClusterIP
  port: 8000

ingress:
  enabled: true
  className: nginx
  hosts:
    - host: promql-translator.local
      paths:
        - path: /
          pathType: Prefix

resources:
  limits:
    cpu: 500m
    memory: 512Mi
  requests:
    cpu: 250m
    memory: 256Mi

aws:
  region: us-east-1
  bedrock:
    enabled: true
  credentials:
    secretName: aws-credentials
```

## Usage

1. Port forward the service:
```bash
kubectl port-forward svc/my-release-promql-translator 8000:8000
```

2. Access the application:
```bash
http://localhost:8000
```

## Security Considerations

- The application requires AWS credentials to access Bedrock services
- Use Kubernetes secrets to manage AWS credentials
- Consider implementing network policies to restrict access
- Enable TLS if exposing the service externally
- Implement proper RBAC policies

## Monitoring

The application can be monitored using Prometheus. Key metrics to monitor:

- API endpoint response times
- Request success/failure rates
- AWS Bedrock API calls
- Memory and CPU usage

## Troubleshooting

Common issues and solutions:

1. AWS Credentials not working:
   - Verify the secret exists and is properly mounted
   - Check AWS region configuration
   - Validate AWS credentials have proper permissions

2. Application not starting:
   - Check pod logs: `kubectl logs -l app=promql-translator`
   - Verify AWS credentials are properly configured
   - Check resource limits and requests

3. Translation failures:
   - Check application logs for AWS Bedrock errors
   - Verify network connectivity to AWS services
   - Check query complexity and length

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This chart is licensed under the MIT License.