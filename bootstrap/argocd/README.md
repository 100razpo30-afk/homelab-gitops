# Argo CD bootstrap

Argo CD уже установлен в кластер Helm-релизом `argocd`. GitOps bootstrap намеренно оставлен шаблоном до подключения удалённого репозитория.

После появления URL репозитория:

1. заменить `REPLACE_WITH_GITOPS_REPO_URL` в `applicationset.yaml.example`;
2. переименовать файл в `applicationset.yaml`;
3. переименовать остальные проверенные `*.yaml.example` в `*.yaml`;
4. применить `project.yaml`, `platform-applications.yaml` и `applicationset.yaml`;
5. первую синхронизацию выполнить вручную через UI.

Автоматические `prune` и `selfHeal` на первом этапе не включаются.

Envoy Gateway использует публичный OCI Helm chart `docker.io/envoyproxy/gateway-helm`. Если установленная версия Argo CD потребует явного подключения OCI registry, его нужно добавить в Settings → Repositories как Helm OCI repository.

