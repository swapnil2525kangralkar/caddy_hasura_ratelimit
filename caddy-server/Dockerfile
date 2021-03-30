FROM caddy:builder AS builder

RUN xcaddy build --with github.com/RussellLuo/caddy-ext/ratelimit

FROM caddy:latest

COPY --from=builder /usr/bin/caddy /usr/bin/caddy