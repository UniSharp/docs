<!-- TITLE: Caddy Server -->
<!-- SUBTITLE: A quick summary of Caddy Server -->

# Caddy Server

## Caddy as system daemon

### by upStart
https://github.com/mholt/caddy/tree/master/dist/init/linux-upstart

### by systemd
https://github.com/mholt/caddy/tree/master/dist/init/linux-systemd


## Run caddy on port 443 only

當 80 port 在 run 本來的 nginx，不想要關掉時。

如果直接啟動如下的 Caddyfile，會遇到 caddyserver 一直說 port 80 已經被佔用，
但是我們其實沒有想要用 caddy 聽 port 80，只想要 443 port 而已

```
https://example.com:443 {
  proxy / localhost:80 {
    transparent
  }
}
```

因此啟動時，多加上 `-disable-http-challenge -http-port 8080` 即可（可使用任意 port，因為我們也不使用它）

disable-http-challenge 官方說明如下：

> Disables the ACME HTTP challenge used for obtaining certificates.

Reference: https://github.com/mholt/caddy/issues/468


## Caddyfile for Laravel Development (fastcgi)

```
localhost:8000 {
    tls off
    root ./public
    log ./storage/logs/caddy-access.log
    errors ./storage/logs/caddy-error.log
	  limits 10m

    fastcgi / 127.0.0.1:9000 php {
        index index.php
        # 也可以限定路徑
        # path /api
    }

    rewrite {
        to {path} {path}/ /index.php?{query}
    }
}
```
