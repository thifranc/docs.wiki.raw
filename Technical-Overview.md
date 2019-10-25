This guide describes the structure of the [Liquid Investigations][] project and explains how to install it for development and production. It assumes a working knowledge of the [Unix shell][], [Git][], [Docker][] and the [HashiStack][].

[Liquid Investigations]: https://liquidinvestigations.github.io/
[Unix shell]: https://en.wikipedia.org/wiki/Unix_shell
[Git]: https://git-scm.com/
[Docker]: https://en.wikipedia.org/wiki/Docker_(software)
[HashiStack]: https://www.hashicorp.com/cloud-operating-model

## Components
Liquid Investigations is a bundle of applications, hosted together on a cluster, with a common authentication layer. Here are the main components:

* [cluster][]: automates [Nomad][], [Consul][] and [Vault][] to spin up a cluster
* [node][]: deploys the Liquid Investigations bundle on the cluster
* [core][]: manages users and provides OAuth2 [SSO][] for the apps
* [authproxy][]: wraps each app, functions as an SSO client, connected to `core`
* [Rocket.Chat][]: real-time chat, similar to IRC and Slack
* [Nextcloud][]: file sharing
* [Hoover][]: search in collections of documents
* [DokuWiki][]: [wiki][] for the users to organize their research and internal documentation
* [Hypothesis][]: annotate documents in `hoover`, `nextcloud` and `dokuwiki`
* [CodiMD][]: realtime collaborative [Markdown][] editor

[cluster]: https://github.com/liquidinvestigations/cluster
[Nomad]: https://www.nomadproject.io/
[Consul]: https://www.consul.io/
[Vault]: https://www.vaultproject.io/
[node]: https://github.com/liquidinvestigations/node
[core]: https://github.com/liquidinvestigations/core
[SSO]: https://en.wikipedia.org/wiki/Single_sign-on
[authproxy]: https://github.com/liquidinvestigations/authproxy
[Rocket.Chat]: https://rocket.chat/
[Nextcloud]: https://github.com/liquidinvestigations/liquid-nextcloud
[Hoover]: https://github.com/liquidinvestigations/h
[DokuWiki]: https://github.com/liquidinvestigations/liquid-dokuwiki
[wiki]: https://en.wikipedia.org/wiki/Wiki
[Hypothesis]: https://github.com/liquidinvestigations/h
[CodiMD]: https://github.com/liquidinvestigations/codimd-server
[Markdown]: https://en.wikipedia.org/wiki/Markdown

## Installation
*TODO*
