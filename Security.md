## Reporting Security Bugs

Please report all security-related bugs at rcij@riseup.net (pgp: 0x8234F8D4A624D9F4).

## Securing Production Servers

- set up encrypted storage
- firewall off the Nomad network interface
- [Enable HTTPS](https://github.com/liquidinvestigations/node/blob/a3ab525e108542d1aa811df9480334fc27cb446d/examples/liquid.ini#L88) and ensure the certificates are valid
- [Enable 2 factor authentication](https://github.com/liquidinvestigations/node/blob/a3ab525e108542d1aa811df9480334fc27cb446d/examples/liquid.ini#L57)
- [Enable auto logout](https://github.com/liquidinvestigations/node/blob/20ece5af24e17e0321265b5abc683455a9a2225c/examples/liquid.ini#L54)

Follow the [[Maintenance]] page on keeping the system up to date and run the latest security patches.

## Disclaimer

TODO