# keycloak-traefik
Keycloak with Traefik Proxy

## Usage
### Clone Repo and create certs directory and acme.json file for traefik-proxy
```
git clone https://github.com/mustafaarif/keycloak-traefik.git
cd traefik-proxy
mkdir certs && cd certs
touch acme.json
chmod 600 acme.json
```
### Update traefik-docker.env
```
CF_API_EMAIL=<cloudflare_email>
CF_DNS_API_TOKEN=<api_token_from_cloudflare>
PRIMARY_DOMAIN=<primary_domain>
TRAEFIK_SSLEMAIL=<ssl_email>
```
### Start Traefik Container
```
docker compose up -d
```
