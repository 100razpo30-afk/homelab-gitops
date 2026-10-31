# Argo CD

Argo CD установлен как bootstrap-компонент обычным Helm-релизом.

- release: `argocd`;
- namespace: `argocd`;
- chart: `argo-cd`;
- chart version: `10.11.6`;
- application version: `v3.5.6`;
- repository: `https://argoproj.github.io/argo-helm`.

TLS завершается на общем Envoy Gateway, поэтому `argocd-server` работает внутри кластера в insecure-режиме по HTTP. Внешний адрес остаётся HTTPS: `https://argocd.local.lan`.

На текущем этапе Argo CD не подключён к Git-репозиторию, Applications не созданы, автоматическая синхронизация и prune не включены.

