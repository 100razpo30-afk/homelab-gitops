# Shared Gateway

Общий Envoy Gateway принимает HTTP/HTTPS-трафик приложений на VIP MetalLB `192.168.1.150`.

- HTTP `:80` перенаправляется на HTTPS;
- HTTPS `:443` завершает TLS на wildcard-сертификате `*.local.lan`;
- маршруты приложений находятся рядом с соответствующими приложениями;
- общий redirect находится здесь, потому что относится к listener всего Gateway.

