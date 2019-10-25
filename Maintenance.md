## Upgrades
At some point after installing, you'll want to upgrade to a newer version of the Liquid bundle.

1. Update the `cluster` to version `x.y.z`:
    ```shell
    cd /opt/cluster
    git fetch
    git checkout vx.y.z
    # check for new settings in `examples/cluster.ini` and add them to `cluster.ini`
    bin/docker.sh --rm --pull
    ```
2. Update `liquid` to version `x.y.z`:
    ```shell
    cd /opt/node
    git fetch
    git checkout vx.y.z
    # check for new settings in `examples/liquid.ini` and add them to `liquid.ini`
    ./liquid deploy
    ```

## Shutting down
To shut down the bundle, stop the cluster container, with a generous timeout:
```shell
docker stop -t 120 cluster 
```
