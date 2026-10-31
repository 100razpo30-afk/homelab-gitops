# Monitoring

Текущий Helm-релиз:

- release: `vm-stack`;
- namespace: `monitoring`;
- chart: `victoria-metrics-k8s-stack`;
- version: `0.97.0`;
- repository: `https://victoriametrics.github.io/helm-charts/`.

`values.yaml` содержит только явно заданные значения текущего релиза. Каталог `config` пока содержит публичный HTTPRoute Grafana.

