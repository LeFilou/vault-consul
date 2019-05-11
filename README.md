# Vault-Consul

A docker-compose of Vault using a Consul backend.

### Installing

Init vault and save the root token and the unseal keys in keys.txt
```
export VAULT_ADDR=http://127.0.0.1:8200
alias vault='docker-compose exec vault vault "$@"'
vault operator init -address=${VAULT_ADDR} > ./keys.txt
```
Unseal vault with the unseal keys

```
vault operator unseal -address=${VAULT_ADDR} KEY1
vault operator unseal -address=${VAULT_ADDR} KEY2
vault operator unseal -address=${VAULT_ADDR} KEY3
```

Authenticate to the server using the vault’s root token
```
vault auth -address=${VAULT_ADDR} ROOT_TOKEN
```