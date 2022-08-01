# Browser configuration with caching

### Install Tor browser portable edition

* Go to https://www.torproject.org/download/, select the operating system of your choice and plug in your removable media
* Your portable Tor browser will be downloaded on to your USB key or SD card
* Rename folder to "LIQUID", put on desktop


###  Improve your Tor hosting performance by hacking up your Tor browser settings 

These are also hard to set-up for normal user, they have to hunt down many browser settings in about:preferences.

* re-enable browser cache following https://2019.www.torproject.org/projects/torbrowser/design/ section "disk avoidance"
 > tried that last time and did not work; maybe something changed?
 > change browser.cache.disk.enable, browser.cache.offline.enable, signon.rememberSignons, browser.formfill.enable and many others force browser to use HTTP/2
* "SPDY and HTTP/2 are currently disabled by setting the Firefox preferences" https://2019.www.torproject.org/projects/torbrowser/design/
* I might have tried this in the past
* change network.http.spdy.enabled, network.http.spdy.enabled.v2, network.http.spdy.enabled.v3, network.http.spdy.enabled.v3-1, network.http.spdy.enabled.http2, network.http.spdy.enabled.http2draft, network.http.altsvc.enabled, and network.http.altsvc.oe
* tune HTTP/1 configurations to use more parallel connections -- "net.http.max-connections-per-server" http://kb.mozillazine.org/Category:Tweaking_preferences
* re-enable "SSL+TLS session resumption"
* change security.ssl.disable_session_identifiers


### advise users to keep separate tor browser install just for accessing liquid (since it's insecure for anything else)* 


***


Back to our detailed [User Guide](https://github.com/liquidinvestigations/docs/wiki/User-Guide).