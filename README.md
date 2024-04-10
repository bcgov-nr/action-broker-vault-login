# Broker Vault Login V1

This action logins the service to Vault, so that automation can **temporarily** access the service's secrets.

The output of this action is a VAULT_TOKEN environment variable. Do not send an unwrapped token outside of the action.

If you encounter an error, ensure that the Broker URL is correct, and your token is valid.

### Usage Notes

It is recommended that:
* the automation never stores the service's secrets on disk.
* the requestor uses the token.
* usage of the secrets should end upon intention closure.

The output Vault token cannot be renewed. A continuously running service (server, serverless function, etc.) should provision an AppRole secret instead. See: https://github.com/bcgov-nr/action-broker-vault-provision

# Broker Documentation

Please refer to the [NR Broker Repository](https://github.com/bcgov-nr/nr-broker) for full usage details.

# Usage

<!-- start usage -->
```yaml
- uses: bcgov-nr/action-broker-vault-login@v1
  with:
    # The token of the action containing the service to use to login as
    action_token: ''

    # The broker url.
    # Default: 'https://broker.io.nrs.gov.bc.ca'
    broker_url: ''

    # The service's application role id in vault. Setting this is recommended to avoid environment mismatch.
    role_id: ''

    # The vault url.
    # Default: https://knox.io.nrs.gov.bc.ca
    vault_url: ''

    # If the token should be returned wrapped. This must be set to true if the
    # action will send the token to an external system.
    # Default: false
    wrap_token: ''
```
<!-- end usage -->

# Output

This action outputs the Vault token as an environment variable.

### VAULT_TOKEN

This is the Vault token that can be used to access the service's secrets. If the input wrap_token is set to true, this will be a wrapping token and NOT the token you can directly use.

# License

The scripts and documentation in this project are released under the [Apache License](LICENSE)

