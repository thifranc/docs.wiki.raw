First make sure your system meets the [[Hardware requirements]].

1. Install `cluster` following the [instructions in the Readme](https://github.com/liquidinvestigations/cluster#quick-start). We recommend you check out the repo as `/opt/cluster`, the rest of the wiki assumes this path.
```shell
sudo -p /opt/cluster
sudo chown $(whoami) /opt/cluster
cd /opt
git clone git@github.com:liquidinvestigations/cluster.git
```
2. Install `node` following the [instructions in the Readme](https://github.com/liquidinvestigations/node#installation). We recommend you check out the repo as `/opt/node`, the rest of the wiki assumes this path.
```shell
sudo -p /opt/node
sudo chown $(whoami) /opt/node
cd /opt
git clone git@github.com:liquidinvestigations/node.git
```

Go to [[User Guide]] for instructions on creating users and granting access. For development tips, go to [[Hacking]].

Follow the [[Maintenance]] page on how to keep the system up to date.