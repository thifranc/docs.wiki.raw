## Overview 

The first part of January started with a business need for indexing new collections and the teams' need for re-indexing old ones. However, issues were identified during the indexing process that needed to be isolated and fixed before moving forward. So on the first two weeks we are solely focusing on this goal.


***

For more details, checkout the **weekly** highlights and release notes.

## Highlights

**10th -> 17th Jan**
* started implementing tracing on indexing related events, which helps to get more in depth information about progress within the indexing process
* researched and started implementing Prefect, with the intent to replace the in house built task management system within the indexing process; 
  * the reasoning behind this decision is that the current solution brings too much overhead whenever something  needs to be tracked down or fixed; Prefect offers better error handling and faster reset capabilities, if indexing fails mid process.


**17th -> 24th Jan**
* Prefect implementation continues
* The new hardware arrived in Bucharest
* The Dev team started conversations with Kubernetes consultants to get a big picture of what are the viable options for switching from Nomad to Kubernetes, under what circumstances and what limitations
* The Dev team will still remain focused on 
  * fixing the indexing issues
  * get the new staging infrastructure up and running, with a relevantly sized test data indexed on it

**24th -> 31th Jan**
* Prefect turned out to not be the most suitable option for our use case. Other tools were researched, such as Dask and Apache Airflow; neither seem to fit our full set of requirements. 
* Indexing performance still remains an ongoing issue that is being worked on.


> ## Release notes 
> ### Snoop
>version 0.4.2
>- improve zipkin traces
>version 0.4.1
>- fix type error in passing an int TASK_COUNT to celery
>version 0.4.0
>- add env SNOOP_WORKER_COUNT for celery process count
>- add envs SNOOP_STATS_ES_{URL,PREFIX} for task completeness stats
>- fix bug where dispatching tasks would OOM
> ### Node
>version 0.7.1
>- use zipkin with kibana and elasticsearch
>
>version 0.7.0
>
> FEATURES:
>- [configure](https://github.com/liquidinvestigations/node/blob/0553a4610c1a0c6c0dd26c5fd02390a98d32f76f/examples/liquid.ini#L156-L157) snoop worker memory limit and worker process count in addition to container count
>- set 32 day retention policy for influxdb, prometheus and elasticsearch x-pack metrics
>- enabled elasticsearch-based counters for task statistics (no configuration needed)
>
> BUG FIXES:
>- fixed python memory leak when dispatching existing jobs