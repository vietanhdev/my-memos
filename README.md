# My Memos - Personal setup of Memos for engineering

## Setup HTTPS (on custom port)

- Install Acme.sh + cronjob for reissuing certs automatically.
- Create a Cloudflare token (for DNS update in the target domain) in <https://dash.cloudflare.com/profile/api-tokens>. This token will be used by Acme.sh for DNS-challenge.
- Fill the below export commands with obtained values.
- Issue SSL certs:

```
export CF_Email="<cloudflare_email>"
export CF_Token="<cloudflare_token>"
acme.sh --issue -d memos.vietanh.dev --dns dns_cf
```

- Install certs:

```
acme.sh --install-cert -d memos.vietanh.dev \
--key-file       key.pem  \
--fullchain-file cert.pem
```

## Run server

```
docker-compose up -d
```
