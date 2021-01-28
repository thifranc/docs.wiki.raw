## Upgrades
At some point after installing, you'll want to upgrade to a newer version of the Liquid bundle.

Watch out for breaking changes in the configuration by looking at the changelogs (tag messages) in:

- [the node releases page](https://github.com/liquidinvestigations/node/releases)
- [the cluster releases page](https://github.com/liquidinvestigations/cluster/releases)

### 1. Update the `cluster` to [version `X.Y.Z`](https://github.com/liquidinvestigations/cluster/releases):

    cd /opt/cluster
    git fetch -ap
    git checkout vX.Y.Z
    # check for new settings in `examples/cluster.ini` and add them to `cluster.ini`
    bin/docker.sh --rm --pull --image liquidinvestigations/cluster:X.Y.Z
    # wait for services to be ready
    docker exec cluster ./cluster.py wait


### 2. Update`node` to [version `X.Y.Z`](https://github.com/liquidinvestigations/node/releases):

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

If Nomad isn't configured to drain jobs (or the drain operation fails) you may also need to kill all containers it left behind:

```shell
docker stop $(docker ps -qa)
```

## Clean reset

Some [Nomad versions](https://www.nomadproject.io/guides/upgrade/upgrade-specific.html) require clearing the server data for upgrades. In those cases it's best to clear the docker system images too, using the following command sequence.

```bash
./liquid halt
docker stop -t 120 cluster
docker stop $(docker ps -qa)
docker system prune --all --force --volumes
sudo rm -rf /opt/cluster/var/nomad
```

... and continue with deploying normally as described in the beginning of this article:
```bash
cd /opt/cluster
git fetch -ap
git checkout vX.Y.Z
bin/docker.sh --rm --pull --image liquidinvestigations/cluster:X.Y.Z
docker exec cluster ./cluster.py wait

cd /opt/node
git fetch -ap
git checkout vX.Y.Z
./liquid deploy
```

_Note:_ if the `docker system prune --all --force --volumes` command takes too long to finish, `sudo systemctl restart docker` and re-run it.

## Backup

run `./liquid backup [OPTIONS] $DIR` to back up the system. 

Optional parameters to specify which parts of the system will be backed up:

`--no-apps`             : excludes app data from backup  
`--no-collections`      : excludes collections from backup  
`--no-pg`               : excludes collection databases from backup  
`--no-es`               : excludes collection es snapshots from backup  
`--no-blobs`            : excludes collection blobs (**B**inary **L**arge **OB**jects) from backup  
`--collection $NAME`    : backup specific collection

When no optional parameter is given, the whole system will be backed up.

## Restore 

Make sure a clean system is installed before starting with the restore process.

Restoring apps: `./liquid restore-apps $DIR`

Restoring collections: `./liquid restore-all-collections $DIR`

_Note:_ The collections have to be disabled in the `liquid.ini` to be restored. After the restore process is finished the collections have to be enabled in the `liquid.ini` again to be accessible.

To finish the restore process run `./liquid deploy`.


## Changing domain name

After changing the upstream network configuration, you will also have to change the following:

- domain in `liquid.ini`
- change domain under `volumes/nextcloud/nextcloud/config/config.php` (it appears two times) 


### Issues after domain change

#### Hypothesis

Bulk changing of annotation target URLs is not supported: [docs page](https://web.hypothes.is/help/how-to-establish-or-avoid-document-equivalence-in-the-hypothesis-system/) 

Since none of our services export those markers, the URLs in Hypothesis will be wrong.

#### HTTPS certificates

HTTPS certificates are not automatically removed. See the [[Admin FAQ]] for more details.

#### 

## Other problems

Use the [[Admin FAQ]] for miscellaneous operating details and the [[Security]] page on how to keep a production system secure.