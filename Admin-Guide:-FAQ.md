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

Try [running a clean reset](https://github.com/liquidinvestigations/docs/wiki/Maintenance#clean-reset). Watch out for [docker daemon GOMAXPROCS](https://github.com/liquidinvestigations/cluster/blob/474f0fd4910bee7e70a1ad09771f9c8033d7d63e/examples/registry-systemd-override.conf#L3) if you are running on many cores.

Nomad errors will be available in the Nomad UI after navigating to the job.

## InfluxDB doesn't start

Running the `cluster` script will fail with:

    influxdb: check "http" is missing


If configured with less than 8GB of RAM, after a few months of time pass, InfluxDB will run out of memory. See [this issue](https://github.com/liquidinvestigations/cluster/issues/125#issuecomment-819422765) for more details.

We have 3 ways to work around this problem:
- Disable `influxdb` from `cluster.ini`:
  - A few non-critical dashboards under Grafana will fail to load.
  - Steps:
    1. In section `[cluster]` set replace `run_jobs = all` with `run_jobs = cluster-fabio,prometheus,grafana,telegraf,dnsmasq,registry`
    2. Run `docker restart cluster`
    3. Stop the `influxdb` job from the Nomad UI, if it's still running.
- Wipe the `influxdb` volume
  - Temporary fix, RAM will exceed limit again at the same speed as first time
  - Steps:
    1. Stop all docker containers: `docker stop $(docker ps -q)`
    2. Check the volume directory: it's the value in `cluster.ini` section `[nomad_meta]` key `cluster_volumes =`, by default is set to `/opt/cluster/var/volumes/`
    3. Remove the `influxdb` directory from underneath it: by default `sudo rm -rf /opt/cluster/var/volumes/influxdb`
- Increase `influxdb` memory limit to some value `> 6000 mb`
  - In `cluster.ini` it's key `influxdb_memory_limit`, set this to a value around 6000-8000
  - On multi-node setups, more RAM will be needed

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
- do a `docker login` with new credentials on that machine