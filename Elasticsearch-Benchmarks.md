For benchmarking searches we use [esrally](https://github.com/elastic/rally).

It can be used to either benchmark an existing cluster or create a temporary one just for benchmarking purposes.

We recommend first running rally with a temporary cluster, using the [default pipeline](https://esrally.readthedocs.io/en/stable/pipelines.html#pipelines) while setting [`--distribution-version=6.8.3`](https://github.com/liquidinvestigations/node/blob/b364b611b2d4a4a1b57c8c8aad1f403f6c9d60a6/templates/hoover-deps.nomad#L5).

Please run the following [tracks](https://esrally.readthedocs.io/en/stable/race.html#list-tracks):

- geopoint
- geonames
- http_logs

Check the [esrally documentation](https://esrally.readthedocs.io/en/stable/recipes.html#benchmarking-an-existing-cluster) on how to benchmark an existing cluster. The node addresses can be found in the Nomad UI.

## tl;dr
```shell
sudo apt install default-jre-headless
export JAVA_HOME=$(readlink -f /usr/bin/java | sed "s:bin/java::")
pip3 install esrally
esrally configure
esrally --distribution-version=6.8.3
```
