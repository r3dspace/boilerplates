# 📄 Caddy docker compose template

Caddy is a versatile and powerful web server that simplifies the process of setting up and managing web applications, while also providing advanced features and customization options.


## 🛠️ Setup by docker compose example

To use the example in this repository, you will need to create a Docker network called `net_rev-porxy`.

```bash
docker network create net_rev-proxy
```

Add the frontend of your other containers to this network to make them accessible via Caddy.

> [!NOTE]
> You will not need to expose your container port using the `ports:` option.

```yml
---
networks:
  rev-proxy:
    name: net_rev-proxy
    external: true

services:
  whoami:
    image: traefik/whoami
    networks:
      - rev-proxy
    command:
       - --port=8080
       - --name=iamfoo
```


## ⚙️ Caddy most used commands

Reload Caddyfile:

```bash
docker compose exec -w /etc/caddy caddy caddy reload
```

Reformat Caddyfile:

```bash
docker compose exec -w /etc/caddy caddy caddy fmt --overwrite
```


## 🔗 Ressources

A list of ressources:

🔗 [Caddy docs](https://caddyserver.com/docs/) \
🔗 [Docker hub - Caddy](https://hub.docker.com/_/caddy)