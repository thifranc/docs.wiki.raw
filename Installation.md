First make sure your system meets the [[Hardware requirements]].

1. Checkout [`cluster`](https://github.com/liquidinvestigations/cluster). We recommend you check out the repo as `/opt/cluster`, the rest of the wiki assumes this path.
```shell
sudo mkdir /opt/cluster
sudo chown $(whoami) /opt/cluster
cd /opt
git clone https://github.com/liquidinvestigations/cluster.git
```
2. Follow the [instructions in the Readme](https://github.com/liquidinvestigations/cluster#quick-start).
3. Checkout [`node`](https://github.com/liquidinvestigations/node) . We recommend you check out the repo as `/opt/node`, the rest of the wiki assumes this path.
```shell
sudo mkdir /opt/node
sudo chown $(whoami) /opt/node
cd /opt
git clone https://github.com/liquidinvestigations/node.git
```
4. Install `node` following the [instructions in the Readme](https://github.com/liquidinvestigations/node#installation)

Go to [[User Guide]] for instructions on creating users and granting access. For development tips, go to [[Development]].

Follow the [[Maintenance]] page on how to keep the system up to date.
