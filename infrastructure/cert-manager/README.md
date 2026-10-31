# cert-manager

Текущий Helm-релиз:

- release: `cert-manager`;
- namespace: `cert-manager`;
- chart: `cert-manager`;
- version: `v1.21.3`;
- repository: `https://charts.jetstack.io`;
- values: `crds.enabled=true`.

Каталог `config` содержит локальный CA и ClusterIssuer. Сам Helm-релиз будет оформлен как Argo CD Application на этапе bootstrap.

