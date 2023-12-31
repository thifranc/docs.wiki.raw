# Single Node Configuration

To run the Liquid Investigations bundle you will need, at a minimum:

* A single Linux system with
  * 28 GB RAM (no Hoover optional features enabled), or 50 GB RAM (all Hoover optional features enabled)
  * 300 GB SSD array
  * 1 TB HDD/NAS array
* Docker version 18 or newer
* Python 3.6+
* pipenv

A system in this configuration should be able to handle about 200 GB of Hoover source data while also running all the bundled applications, see the next section for details.

Liquid Investigations has only been tested on Ubuntu 18 & 20 LTS, Debian 10 and CentOS.


## Storage

It's highly recommended to use RAID-5 (or better) for both the SSD and the HDD volumes. Backups should also be saved on a different machine, or at least on a different disk array.

Liquid Investigations requires **SSD storage (either SATA or M.2)** to be available for:
- operating system and host system packages - `20 GB`
- docker images - `50 GB`
- system runtime metrics - `~30 GB` for the last 4 weeks of system metrics
- application data - max. `50 GB` for wiki, chat, pads, annotations
- hoover elasticsearch and databases storage - ~0.6 X size of source data

The following can be stored on **slower storage, HDD or NAS**:
- hoover source collection data - includes files uploaded by users
- hoover internal data (data blobs) - ~3 X size of source data


Backups also take space: expect application data to be 5-50GB / snapshot, and collection backups to take as much as 2X the source data.

So, for example, you need to be able to search through **2TB** of source collection data. You need at least:

- server HDD array: 2TB (source) + 6TB (blobs) = **8TB**
- server SSD array: 1.2TB (hoover database and elasticsearch) + .15TB (everything else in the list) = **1.35TB**
- backup machine: 2 * 2 * 2TB (2 backups for each collection processed) + 240GB (12 application snapshots) = **8.24TB**

Note: the example *2 TB* of source data mentioned above should be manually divided into around *10 collections*, following the [Collection Size Limit section](https://github.com/liquidinvestigations/docs/wiki/Admin-Guide%3A-Manage-Hoover-collections#collection-size-limit).

## Memory

The minimal memory requirement to run every app is 28GB.
- When the number of concurrent users reaches around 50-100, an extra 8GB of RAM is needed to scale the number of web server and authentication proxy containers. 
- The memory requirement for hoover's elasticsearch and postgresql depends on source collection data size:
  - **~1TB source** data: machine requires in total **32GB of RAM**
    - 5GB elasticsearch, 3GB postgresql
    - 7GB of additional RAM to be available to the OS (will be used as filesystem cache)
  - **~3TB source** data: machine requires in total **64GB of RAM**
    - 16GB elasticsearch, 6GB postgresql
    - 22GB of additional RAM to be used as filesystem cache
  - **more than 8TB source** data: machine requires in total **128GB RAM**
    - 30GB elasticsearch, 10GB postgresql
    - 40GB of additional RAM to be used as filesystem cache


## Compute

Use a machine with at least 4 CPU cores. The system has been seen to scale well to 50 cores. Enable hyperthreading if available.


## Example setup

Most of the work has been done on *gaming computers* with these specifications. Prices have been sampled in May 2020 from european Amazon.

- ~2017 intel i7 with 8 cores and hyper-threading (e.g. intel i7-9700K, $400)
- 64 GB DDR4 (4x16 kit, bulk, $300)
- 2 x 2 TB SSD PCIe M.2 arranged in software RAID-1 (intel 665p, $280 each)
- 3 x 8 TB HDD arranged in software RAID-5 (WD red, $220 each)
- compatible motherboard, case, 800 watt power unit (total $350)
- gigabit Ethernet internet connection

Setup cost total: ~$2300

With some fine-tuning, this single node system has served around 120 concurrent users searching through 3 TB of source data.

### Extending the setup

Processing speed may be improved by using adding more workers to the cluster. These can be flexibly added and removed; see the next section.


# Multi Node Configuration

The single-node setup can be extended to multiple machines if needed.

- Use at least 16 GB of RAM and 100 GB of local SSD storage for each worker node in the cluster.
- Use at least 32 GB of RAM for the server node. Also, the storage only need to be connected to this server node.
- Connect all the nodes using a firewalled VPN in the same IPv4 /24 subnet.
- A 1Gbps LAN should give acceptable performance.