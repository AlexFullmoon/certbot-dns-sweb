Certbot Docker image with DNS plugin for Spaceweb (sweb.ru). Uses [curserio/certbot-dns-sweb](https://github.com/curserio/certbot-dns-sweb) plugin.

### Usage

Example docker compose:
```yml
services:
  certbot:
    image: ghcr.io/AlexFullmoon/certbot-dns-sweb
    volumes:
      - ./sweb.ini:/etc/letsencrypt/sweb.ini:ro
      - ./certs:/etc/letsencrypt
    command: >
      certonly
      --non-interactive
      --authenticator dns-sweb
      --dns-sweb-credentials /etc/letsencrypt/sweb.ini
      --dns-sweb-propagation-seconds 900
      --email your@email.com
      --agree-tos
      -d example.com
      -d '*.example.com'
```
sweb.ini contains credentials, e.g.
```ini
dns_sweb_login = your_login_here
dns_sweb_password = your_password_here
```

Every part is licensed under its respective license.