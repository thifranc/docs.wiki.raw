## Upgrades
At some point after installing, you'll want to upgrade to a newer version of the Liquid bundle.

Watch out for breaking changes in the configuration by looking at the changelogs (tag messages) in:

- [the node releases page](https://github.com/liquidinvestigations/node/releases)
- [the cluster releases page](https://github.com/liquidinvestigations/cluster/releases)

### 1. Update the `cluster` to version `X.Y.Z`:

    cd /opt/cluster
    git fetch
    git checkout vX.Y.Z
    # check for new settings in `examples/cluster.ini` and add them to `cluster.ini`
    bin/docker.sh --rm --pull --image=liquidinvestigations/cluster:X.Y.Z
    # wait for services to be ready
    docker exec cluster ./cluster.py wait


### 2. Update `liquid` to version `X.Y.Z`:

    cd /opt/node
    git fetch
    git checkout vX.Y.Z
    # check for new settings in `examples/liquid.ini` and add them to `liquid.ini`
    ./liquid deploy


## Shutting down

To shut down the bundle, stop the cluster container, with a generous timeout:
```shell
docker stop -t 120 cluster 
```

## Clean restarts

Some [Nomad versions](https://www.nomadproject.io/guides/upgrade/upgrade-specific.html) require clearing the server data for upgrades. In those cases it's best to clear the docker system images too, using the following command sequence.

```bash
docker stop -t 120 cluster
docker stop $(docker ps -qa)
docker system prune --all --force --volumes
```

... and continue with deploying normally as described in the beginning of this article:
```bash
cd /opt/cluster
bin/docker.sh --rm --pull --image=liquidinvestigations/cluster:X.Y.Z
docker exec cluster ./cluster.py wait

cd /opt/node
./liquid deploy
```

_Note:_ if the `docker system prune --all --force --volumes` command takes too long to finish, `sudo systemctl restart docker` and re-run it.

## Other problems

Use the [[Admin FAQ]] for miscellaneous operating details and the [[Security]] page on how to keep a production system secure.