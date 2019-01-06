mkdir -p /mnt/vault/config

edit /mnt/vault/config/config.hcl

```
default_lease_ttl = "168h"
max_lease_ttl = "720h"
ui = true
api_addr = "https://0.0.0.0:8200"
log_level = "debug"

listener "tcp" {
  address = "0.0.0.0:8200"
  tls_disable = "true"
}

storage "file" {
  path = "/vault/"
}
```
  
chmod -R 777 /mnt/vault

docker run -v /mnt/vault/:/vault/ -p 8200:8200 --cap-add IPC_LOCK -e 'VAULT_ADDR=http://127.0.0.1:8200' vault server

docker ps
docker exec -it faf8e65d6e35    /bin/sh

`vault operator init`

`vault operator unseal`
