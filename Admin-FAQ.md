# Operating Liquid Investigations Servers

## Something broke, how do I fix it?
* Check [issues labelled `bug`](https://github.com/orgs/liquidinvestigations/projects/1?card_filter_query=label%3Abug#card-29263439) on the public board. If the bug is not tracked please add it.
* Ask on Slack! **TODO** how to get on Slack

[issues labelled `bug`]: https://github.com/orgs/liquidinvestigations/projects/1?card_filter_query=label%3Abug

## Nomad won't schedule jobs
Try [running a clean reset](https://github.com/liquidinvestigations/docs/wiki/Maintenance#clean-reset). Watch out for [docker daemon GOMAXPROCS](https://github.com/liquidinvestigations/cluster/blob/474f0fd4910bee7e70a1ad09771f9c8033d7d63e/examples/registry-systemd-override.conf#L3) if you are running on many cores.
