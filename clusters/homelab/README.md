# Cluster: homelab

Каталог описывает набор Argo CD Applications для единственного локального кластера.

После создания удалённого Git-репозитория шаблон из `bootstrap/argocd/applicationset.yaml.example` будет дополнен настоящим `repoURL` и станет точкой входа для следующих приложений:

- `contest`;
- `kontent`;
- `cert-manager-config`;
- `metallb-config`;
- `gateway-config`;
- `monitoring-config`.

Helm-релизы контроллеров описываются отдельно, потому что их источником является Helm registry/repository, а не директория этого Git-репозитория.

