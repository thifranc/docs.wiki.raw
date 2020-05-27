To run the Liquid Investigations bundle you will need, at a minimum:

* A single Linux system with
  * 28GB RAM
  * 250GB SSD array
  * 1TB HDD/NAS array
* Docker version 18 or newer
* Python 3.6+
* pipenv

A system in this configuration should be able to handle about 200GB of Hoover source data while also running all the bundled applications, see the next section for details.

Liquid Investigations has only been tested on Ubuntu 18, Debian 10 and CentOS.


## Storage

Liquid Investigations requires SSD storage (either SATA or M.2) to be available for:
- docker images -- 20GB
- application data -- max. 50GB for wiki, chat, pads, annotations
- system runtime metrics -- ~30GB for the last 4 weeks of system metrics
- hoover elasticsearch and databases storage -- ~0.6 X size of source data 

The following can be stored on slower storage, HDD or NAS:
- hoover source collection data - includes files uploaded by users
- hoover internal data (data blobs) -- ~2.5 X size of source data


So, for example, you need to be able to search through **2TB** of source collection data. You need at least:

- 2TB (source) + 5TB (blobs) = **7TB of HDD storage**
- 1.2TB (hoover database and elasticsearch) + .1TB (everything else in the list) = **1.3TB of SSD storage**


It's highly recommended to use RAID-5 (or better) for both the SSD and the HDD volumes.

Backups also take space: expect application data to be around 20GB / snapshot, and collection backups to take around the same space as the source data.

## Memory

The minimal memory requirement to run every app is 28GB.
- When the number of concurrent users reaches around 50, an extra 8GB of RAM is needed to scale the number of web server and authentication proxy containers. 
- The memory requirement for hoover's elasticsearch and postgresql depends on source collection data size:
  - **~1TB source** data: machine requires in total **32GB of RAM**
    - 5GB elasticsearch, 3GB postgresql
    - 7GB of additional RAM to be available to the OS (will be used as filesystem cache)
  - **~3TB source** data: machine requires in total **64GB of RAM**
    - 16GB elasticsearch, 6GB postgresql
    - 22GB of additional RAM to be used as filesystem cache
  - **more than 8TB** source data: machine requires in total **128GB RAM**
    - 30GB elasticsearch, 10GB postgresql
    - 40GB of additional RAM to be used as filesystem cache


## Compute

Use a machine with at least 4 CPU cores. The system has been seen to scale well to 50 cores. Enable hyperthreading if available.


## Example setup

Most of the work has been done on *gaming computers* with these specifications. Prices have been sampled in May 2020 from european Amazon.

- ~2017 intel i7 with 8 cores and hyper-threading (e.g. intel i7-9700K, $400)
- 64GB DDR4 (4x16 kit, bulk, $300)
- 2 x 2TB SSD PCIe M.2 arranged in software RAID-1 (intel 665p, $280 each)
- 3 x 8TB HDD arranged in software RAID-5 (WD red, $220 each)
- compatible motherboard, case, 800 watt power unit (total $350)
- gigabit ethernet internet connection

Setup cost total: ~$2300

With some fine tuning, this node has served around 120 concurrent users searching through 3TB of source data.