# Caddy 2.0 with ratelimit - hasura graphql 
![alt text](https://github.com/swapnil2525kangralkar/caddy_hasura_ratelimit/blob/master/rate_limit_hasura_1.gif)

## Pre-requisites

- [Docker](https://docs.docker.com/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Build Custom Caddy image with rate limit
```
cd caddy-server
docker build --tag custom_caddy:0.0.1 .
```
## Usage

- Clone this repo on a machine with a public ip address
- Map your domain name to this ip address
- Edit `Caddyfile` and add your domain (replace `<your-domain.com>` with your domain, don't keep `<>`)
- Edit `docker-compose.yaml` and change `HASURA_GRAPHQL_ADMIN_SECRET` to something secure
- `docker-compose up -d` - execute in directory where docker-compose.yaml 

## Rate Limiting
- In caddyfile change `rate_limit {remote.ip} 120r/m`
- Default: 120 requets per min on ip address

GraphQL endpoint will be `https://<your-domain.com>/v1/graphql`
Console will be available on `https://<your-domain.com>/console`

## Connecting to External Postgres

If you want to connect to an external/existing postgres database, replace `HASURA_GRAPHQL_DATABASE_URL` in `docker-compose.yaml` with your database url. 

**Note: localhost will resolve to the container ip inside a docker container, not the host ip**


