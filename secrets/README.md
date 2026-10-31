# Secrets

В Git нельзя добавлять незашифрованные Kubernetes Secret и реальные пароли.

На текущем этапе Argo CD не управляет следующими существующими Secret:

- `kontent/app-secrets`;
- `kontent/ghcr-secret`;
- `contest/postgre-secret`;
- `contest/ghcr-secret`;
- `cert-manager/local-ca-secret` создаётся объектом `Certificate`.

Следующий этап миграции: установить SOPS, создать ключ age, зашифровать Secret и настроить расшифровку для Argo CD. До этого существующие Secret нельзя удалять из кластера.

