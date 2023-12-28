# Broker Vault Login V1

This action logins the service to vault, so that automation can **temporarily** access the service's secrets.

If you encounter an error, ensure that the Broker URL is correct and your token is valid.

### Usage Notes

It is recommended that:
* the automation never stores the service's secerts on disk.
* the requestor uses the token.
* usage of the secrets should end upon intention closure.

The returned token can not be renewed. A continously running service (server, server-less function, etc.) should provision an approle secret instead.

# Broker Documention

Please refer to the [NR Broker Repository](https://github.com/bcgov-nr/nr-broker) for full usage details.

# Usage

<!-- start usage -->
```yaml
- uses: bcgov-nr/action-broker-vault-login@v1
  with:
    # The token of the action containing the service to use to login as
    action_token: ''

    # The broker url.
    # Default: 'https://nr-broker.apps.silver.devops.gov.bc.ca'
    broker_url: ''

    # The service's application role id in vault. Setting this is recommended to avoid environment mismatch.
    role_id: ''

    # The vault url.
    # Default: https://knox.io.nrs.gov.bc.ca
    vault_url: ''
```
<!-- end usage -->

# Output

This action outputs the intention and action tokens as environment variables.

### VAULT_TOKEN

This is the vault token that can be used to access the service's secrets.

# License

The scripts and documentation in this project are released under the [Apache License](LICENSE)

