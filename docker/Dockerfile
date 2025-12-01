FROM caddy:2.10-builder AS builder

ENV GOPROXY=https://goproxy.cn,direct
ENV GO111MODULE=on

RUN --mount=type=cache,target=/go/pkg/mod \
    --mount=type=cache,target=/root/.cache/go-build \
    xcaddy build \
    --with github.com/caddy-dns/cloudflare \
    --with github.com/caddy-dns/alidns

FROM caddy:2.10

COPY --from=builder /usr/bin/caddy /usr/bin/caddy