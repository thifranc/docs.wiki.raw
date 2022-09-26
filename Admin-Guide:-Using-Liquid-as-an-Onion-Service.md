It's recommended to configure the Tor Hidden Service before starting `./liquid deploy` for the first time, otherwise you may need to follow the [changing domain name](https://github.com/liquidinvestigations/docs/wiki/Maintenance#changing-domain-name) instructions.

Following the "Set up Guide" https://community.torproject.org/onion-services/setup/ you need to finish Step 0 to get a working Tor, first. Having that done, you will need to add the following two lines to your `/etc/tor/torrc` file:

```
HiddenServiceDir /var/lib/tor/liquid
HiddenServicePort 80 10.66.60.1:80
```

After restarting the tor service, you can find the created Onion Service hostname in `/var/lib/tor/liquid/hostname`.

Use the hostname value in `/opt/node/liquid.ini` as `domain`:

```
domain = 0123456789thisisjustaninvalidsampleandnotavvalidonionurl.onion
```
