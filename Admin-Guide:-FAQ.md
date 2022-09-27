# Operating Liquid Investigations Servers

## Something broke, how do I fix it?
* Identify and save logs for failed job in the Nomad UI. Service health check responses are available in the Consul UI.
* Check [issues labelled `bug`](https://github.com/orgs/liquidinvestigations/projects/1?card_filter_query=label%3Abug#card-29263439) on the public board. If the bug is not tracked please add it.
* Ask on Slack!

[issues labelled `bug`]: https://github.com/orgs/liquidinvestigations/projects/1?card_filter_query=label%3Abug

## Invalid HTTPS certificates
There is a limitation with Traefik 1.7: it doesn't update the stored certificates if the configuration changes. This means an administrator will have to wipe the certificates after a change in:

- [domain](https://github.com/liquidinvestigations/node/blob/20ece5af24e17e0321265b5abc683455a9a2225c/examples/liquid.ini#L12)
- [https on/off](https://github.com/liquidinvestigations/node/blob/20ece5af24e17e0321265b5abc683455a9a2225c/examples/liquid.ini#L88)
- [caServer](https://github.com/liquidinvestigations/node/blob/20ece5af24e17e0321265b5abc683455a9a2225c/examples/liquid.ini#L92)

To wipe the certificates one should delete the Consul KV entries `/traefik` and `/liquid/traefik/acme` from the [Consul UI](https://github.com/liquidinvestigations/node/blob/20ece5af24e17e0321265b5abc683455a9a2225c/examples/liquid.ini#L3).

To follow Traefik's progress in getting the HTTPS certificates from LetsEncrypt use the Nomad UI to follow its console output.

## Nomad won't schedule jobs

Try [running a clean reset](https://github.com/liquidinvestigations/docs/wiki/Maintenance#clean-reset). Watch out for [docker daemon GOMAXPROCS](https://github.com/liquidinvestigations/cluster/blob/474f0fd4910bee7e70a1ad09771f9c8033d7d63e/examples/registry-systemd-override.conf#L3) if you are running on many cores. For machines with >32 cores, we recommend configuring docker with `GOMAXPROCS` of 8-12.

Nomad errors will be available in the Nomad UI after navigating to the job.



## Snoop gets stuck when processing

When processing many collections in parallel, one might run out of RabbitMQ memory. To check if this has happened:
- Proxy port `10.66.60.1:9990` from server onto local machine `localhost:9990` using SSH LocalForward configuration.
- Visit `http://localhost:9990/_snoop_rabbit/`, login with username `guest` and password `guest`.
- Look at the "Memory" cell on the "Overview" screen. If it's red, then you're out of memory.

If you're out of RabbitMQ memory, do one of these:
- increase `rabbitmq_memory_limit` to 4+ GB, or
- process less collections at the same time (set `process = off` on some of them, turn on again later)

## Elasticsearch won't index documents / Hypothesis won't save annotations

When the elasticsearch disk exceeds some 90% limit, elasticsearch will lock itself up.

Hypothesis also uses elasticsearch to save annotations, so you'll see the same issue there.

Be sure to free up some disk space first, then run:

```
export ES_ADDR=10.66.60.1:9990/_es
curl  -XPUT "$ES_ADDR/_cluster/settings" -H 'Content-Type: application/json' -d '{"persistent":{"cluster.blocks.read_only":false}}'
curl  -XPUT "$ES_ADDR/_all/_settings" -H 'Content-Type: application/json' -d'{ "index.blocks.read_only_allow_delete" : null } }'
```

... where 10.66.60.1 is the network address configured in cluster.ini and liquid.ini.


For hypothesis, you have to identify the container port opened with `docker ps | grep hypothesis/elasticsearch` and set the ES_ADDR to that `ip:port`. Then, re-run the 2 commands.

## Docker Hub - Download Rate Limit 

Docker Hub has been decreasing their free anonymous download limit. When deploying, you might reach this limit on your host IP.

See [the Docker article on download-rate-limit](https://docs.docker.com/docker-hub/download-rate-limit/).

Temporary work-around:
- create a free Docker Hub account for each instance
- do a `docker login` with new credentials on the machine running `./liquid deploy`.