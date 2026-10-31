# Migration notes

Этот репозиторий пока не подключён к Argo CD и не изменяет живой кластер.

## Что перенесено

- прикладные ресурсы Contest и Kontent;
- PostgreSQL и MinIO с существующими PV/PVC;
- HTTPRoute приложений;
- конфигурация MetalLB и общего Envoy Gateway;
- локальный CA cert-manager;
- HTTPRoute Grafana;
- внешняя конфигурация dnsmasq;
- текущие версии и values установленных Helm-релизов.

Исходные каталоги `contest/k8s` и `kontent/k8s` не удалены.

## Что намеренно не перенесено

- открытые значения из `kontent/k8s/01-secrets.yaml`;
- содержимое существующих `ghcr-secret`;
- любые приватные ключи CA;
- ручной `deploy.sh`, потому что его роль после миграции выполняет Argo CD.

## Известные отличия от живого кластера

Перед первым Sync `kubectl diff` показал:

1. В Git-конфигурации Contest присутствуют `KEYCLOAK_URL`, `KEYCLOAK_REALM` и `KEYCLOAK_CLIENT_ID`, но в живых ConfigMap и Deployment их пока нет. Sync добавит переменные и перезапустит `contest-api`.
2. StatefulSet `kontent/postgres` в кластере использует строку образа `postgres:16-alpine`, а манифест — эквивалентную полную запись `docker.io/library/postgres:16-alpine`. Kubernetes воспримет это как изменение Pod template и выполнит rolling restart.

Остальные перенесённые конфигурационные ресурсы совпадают с живым кластером по server-side diff.

## Безопасный первый запуск

1. Создать Git-репозиторий и заменить placeholder URL в bootstrap-файлах.
2. Установить Argo CD.
3. Переименовать `*.yaml.example` в `*.yaml` после проверки URL.
4. Добавить публичный OCI registry Envoy Gateway в Argo CD при необходимости.
5. Синхронизировать контроллеры по одному: cert-manager, MetalLB, Envoy Gateway, VictoriaMetrics.
6. Синхронизировать `cert-manager-config`, `metallb-config`, `gateway-config`, `monitoring-config`.
7. Убедиться, что существующие Secret сохранены.
8. Синхронизировать `kontent`, затем `contest`, наблюдая за rollout.
9. Только после стабильной работы обсуждать `automated`, `selfHeal` и `prune`.

