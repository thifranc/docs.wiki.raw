Liquid can be used with external HTTPS termination, and with VPN clients.

## Configure HTTPS

Under VPN we can't use the "Let's Encrypt HTTP challenge" we automatically use. Because of this, you must supply your own HTTPS termination, for example using Nginx or Apache. Liquid will run in HTTP mode with HTTPS protocol override, like this:

```
[liquid]
http_protocol_override = https
```

And comment out the `[https]` section to disable it from Liquid:

```
; [https]
```

Each app is hosted of its own subdomain. Here is the full list of subdomains to obtain certificates for:

- `yourdomain.org`
- `hoover.yourdomain.org`
- `dokuwiki.yourdomain.org`
- `rocketchat.yourdomain.org`
- `codimd.yourdomain.org`
- `nextcloud.yourdomain.org`

You can skip the ones that won't be enabled.

After HTTPS termination, forward all traffic to the Liquid server, port `80` (by default `10.66.60.1:80`). 

## Configure VPN and DNS

Set up your own VPN server, clients, and configuration.

If the client VPN server is on the same machine or LAN as the Liquid servers, make sure to firewall off any direct connection into the Cluster Interface (by default IP 10.66.60.1).

The following subdomains must be configured in the DNS configurations for VPN:

- `yourdomain.org`
- `hoover.yourdomain.org`
- `dokuwiki.yourdomain.org`
- `rocketchat.yourdomain.org`
- `codimd.yourdomain.org`
- `nextcloud.yourdomain.org`

These DNS records should point to your own HTTPS termination server configured in the previous section.