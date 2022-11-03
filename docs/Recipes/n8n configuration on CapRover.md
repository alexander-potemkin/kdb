# n8n configuration on CapRover

- enable `5678` container HTTP port
- add GitHub deployment private key & image repository
- enable force https & websocket support
- add following environment variables:

```bash
DB_TYPE=postgresdb
DB_POSTGRESDB_HOST=192.168.0.174
DB_POSTGRESDB_PORT=6432
DB_POSTGRESDB_USER=db_user
DB_POSTGRESDB_PASSWORD=..
DB_POSTGRESDB_DATABASE=db_name
DB_POSTGRESDB_SCHEMA=public

N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_PASSWORD=username
N8N_BASIC_AUTH_USER=password

GENERIC_TIMEZONE=Asia/Tokyo
WEBHOOK_TUNNEL_URL=https://FQDN/
N8N_ENCRYPTION_KEY=..

EXECUTIONS_DATA_PRUNE=true
EXECUTIONS_DATA_MAX_AGE=672

EXTERNAL_HOOK_URL=https://FQDN-statistics-server/api/v1/hook/client_name
```

## Settings comments and meaning

[EXECUTIONS_PROCESS](https://docs.n8n.io/reference/configuration.html#execute-in-same-process)

> ...*in case the workflows are not CPU intensive and they have to start very fast, it is possible to run them all directly in the main-process with this setting.*
> 

[GENERIC_TIMEZONE](https://docs.n8n.io/reference/configuration.html#timezone) with values reference as per [here](https://momentjs.com/timezone/), examples are: `Europe/Moscow`, `Asia/Tokyo`, etc.

[N8N_BASIC_AUTH_ACTIVE, N8N_BASIC_AUTH_PASSWORD, N8N_BASIC_AUTH_USER](https://docs.n8n.io/reference/security.html#basic-auth) - enable HTTP basic user auth. 

[N8N_PROTOCOL & N8N_HOST & N8N_PORT](https://docs.n8n.io/reference/configuration.html#publish) - helps n8n to recognize how it's seen from the outside, not required, if `WEBHOOK_TUNNEL_URL` is specified.

[WEBHOOK_TUNNEL_URL](https://docs.n8n.io/reference/configuration.html#webhook-url) - fully qualified domain name, with http**S** on it

[EXECUTIONS_DATA_MAX_AGE && EXECUTIONS_DATA_PRUNE](https://docs.n8n.io/reference/configuration.html#prune-data)

Delete execution data older than `EXECUTIONS_DATA_MAX_AGE` *hours*.

> ...*prune the execution data. This prevents exceeding the database's capacity and keeping its size moderate. The execution data gets pruned regularly (default: 1-hour interval). All saved execution data older than the max-age will be deleted...*
> 

 

[N8N_ENCRYPTION_KEY](https://docs.n8n.io/reference/configuration.html#encryption-key) - a MUST for a proper work, or encryption keys will get lost