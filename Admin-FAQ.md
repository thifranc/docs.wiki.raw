# Operating Liquid Investigations Servers

When in doubt, 

## Invalid HTTPS certificates

There is a limitation with Traefik 1.7: it doesn't update the stored certificates if the configuration changes. This means an administrator will have to wipe the certificates after a change in:

- [domain](https://github.com/liquidinvestigations/node/blob/20ece5af24e17e0321265b5abc683455a9a2225c/examples/liquid.ini#L12)
- [https on/off](https://github.com/liquidinvestigations/node/blob/20ece5af24e17e0321265b5abc683455a9a2225c/examples/liquid.ini#L88)
- [caServer](https://github.com/liquidinvestigations/node/blob/20ece5af24e17e0321265b5abc683455a9a2225c/examples/liquid.ini#L92)

To wipe the certificates one should delete the Consul KV entries `/traefik` and `/liquid/traefik/acme` from the [Consul UI](https://github.com/liquidinvestigations/node/blob/20ece5af24e17e0321265b5abc683455a9a2225c/examples/liquid.ini#L3).

To follow Traefik's progress in getting the HTTPS certificates from LetsEncrypt use the Nomad UI to follow its console output.

## Nomad won't schedule jobs

Try [running a clean reset](https://github.com/liquidinvestigations/docs/wiki/Maintenance#clean-reset). Watch out for [docker daemon GOMAXPROCS](https://github.com/liquidinvestigations/cluster/blob/474f0fd4910bee7e70a1ad09771f9c8033d7d63e/examples/registry-systemd-override.conf#L3) if you are running on many cores.