# Envoy Gateway

Текущий Helm-релиз:

- release: `eg`;
- namespace: `envoy-gateway-system`;
- OCI chart: `oci://docker.io/envoyproxy/gateway-helm`;
- version: `v1.9.3`;
- custom values отсутствуют.

Helm-релиз устанавливает Gateway API CRD и контроллер. Объекты GatewayClass, Gateway и EnvoyProxy находятся в `infrastructure/gateway/config`.

