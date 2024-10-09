# Create SSL use Certbot

```sh
certbot certonly -d [domain] --expand --manual --key-type rsa --preferred-challenges=http --config-dir ~/workspaces/lets-encrypt --work-dir ~/lets-encrypt --logs-dir ~/workspaces/lets-encrypt
```
