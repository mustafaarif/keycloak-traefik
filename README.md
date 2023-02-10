# keycloak-traefik
Keycloak with Traefik Proxy

## Usage

### Install Docker and Docker Compose
```
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

### Create bridge network
```
docker network create web
```

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
### Update keycloak/.env file 
```
# Fill in random_pass with password generated from `openssl rand -base64 14`
POSTGRES_USER=pstadmin
POSTGRES_PASSWORD=random_pass
POSTGRES_DB=keycloak
KEYCLOAK_ADMIN=keycloak-admin
KEYCLOAK_ADMIN_PASSWORD=random_pass
```
### Create volume dirs for persistent storage
```
mkdir ~/keycloak/dbData
```
### Start KeyCloak Container
```
docker compose up -d
```
