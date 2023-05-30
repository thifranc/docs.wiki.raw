# Liquid using WireGuard and Tails

### Work in progress
***

Liquid can be used in an isolated environment accessible using a WireGuard VPN only. Moreover, a slightly more paranoid setup is using Tails accessing this isolated service.

Consider the generic instruction to use [[Liquid on VPN|Admin Guide: Using Liquid on VPN]], first.

## Setting up the server-side WireGuard VPN

Based on top of the [WireGuard Quick Start](https://www.wireguard.com/quickstart/) you may want to use the [WireGuard installer](https://github.com/angristan/wireguard-install) provided by [angristan at GitHub](https://github.com/angristan). Some unofficial [WireGuard Documentation](https://github.com/pirate/wireguard-docs#readme) is very useful for more advanced setups.

### Install [WireGuard](https://www.wireguard.com/install/)

```shell
sudo apt install wireguard
```

Create a private/public key pair using:

```shell
cd /etc/wireguard
umask 077
wg genkey | tee privatekey | wg pubkey > publickey
```

Create a configuration file at `/etc/wireguard/wg0.conf` using a private IP range like `10.11.12.0/24`:

```ini
[Interface]
Address = 10.11.12.1/32
SaveConfig = true
PostUp = iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE
PreDown = iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE
ListenPort = 51820
PrivateKey = **private server key**

[Peer]
PublicKey = **public client key**
AllowedIPs = 10.11.12.2/32
```

### Start and stop using `wg-quick`

```shell
# start
sudo wg-quick up wg0
# stop
sudo wg-quick down wg0
```

## Adding clients

You'll need the **public** key for every peer and assign an individual IP used on the client side. On the client install WireGuard and create a configuration file `/etc/wireguard/wg0.conf`:

```ini
[Interface]
PrivateKey = **private client key**
Address = 10.11.12.2/32

[Peer]
PublicKey = **public server key**
AllowedIPs = 10.11.12.0/24
Endpoint = **public server ip**:51820
PersistentKeepalive = 25
```

Add the client peer on the server side using:

```shell
# add peer
sudo wg set wg0 peer **public client key** allowed-ips 10.11.12.2
# remove peer
sudo wg set wg0 peer **public client key** remove
```

## Provision Tails to be a peer

Assuming: an existing Tails Persistence layer, a configured Administration user and an enabled Unsafe Browser, start installing WireGuard using `sudo apt update && sudo apt install wireguard`, first. Answer _Install Every Time_ when prompted. Add a client config as above.

Allow incoming and outgoing udp packets by editing `/etc/ferm/ferm.conf`:

```patch
--- /etc/ferm/ferm.conf	2022-12-19 09:43:26.000000000 +0000
+++ ferm.conf	2023-01-12 12:23:14.984001706 +0000
@@ -13,6 +13,11 @@
         chain INPUT {
             policy DROP;
 
+            daddr (**public server ip**/32) {
+                proto udp ACCEPT;
+#		ACCEPT;
+            }
+
             # Established incoming connections are accepted.
             mod state state (ESTABLISHED) ACCEPT;
 
@@ -32,6 +37,11 @@
         chain OUTPUT {
             policy DROP;
 
+            daddr (**public server ip**/32) {
+                proto udp ACCEPT;
+#		ACCEPT;
+            }
+
             # Established outgoing connections are accepted.
             mod state state (ESTABLISHED) ACCEPT;
 
@@ -122,6 +132,7 @@
                 ACCEPT;
             }
 
+
             # Everything else is logged and dropped.
             LOG log-prefix "Dropped outbound packet: " log-level debug log-uid;
             REJECT reject-with icmp-port-unreachable;
```

Apply changes with `service ferm restart`.

## Additional configs for local DNS and Certificates using the Unsafe Browser

Add local DNS setting applying a patch to `/usr/local/sbin/usafe-browser`:

```patch
--- /usr/local/sbin/unsafe-browser	2022-12-19 09:43:26.000000000 +0000
+++ unsafe-browser	2023-01-12 12:24:06.980003349 +0000
@@ -152,6 +152,8 @@
 echo '127.0.0.42 firefox.settings.services.mozilla.com' \
      >> "${CHROOT}"/etc/hosts
 
+echo '10.11.12.1      **servername**.home.arpa hoover.**servername**.home.arpa dokuwiki.**servername**.home.arpa rocketchat.**servername**.home.arpa nextcloud.**servername**.home.arpa codimd.**servername**.home.arpa wikijs.**servername**.home.arpa' >> "${CHROOT}"/etc/hosts
+
 echo "* Starting Unsafe Browser"
 # Do not localize the 5th argument: it becomes WM_CLASS and then GNOME
 # displays the localized app name found in the matching .desktop file;
```