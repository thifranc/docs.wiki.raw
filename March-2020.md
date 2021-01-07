## Overview

Starting March, we have a new student joining our team, at Der Spiegel: Morten.
The month also started with important features being finalized and ready to production: a single Snoop instance for all collections, import/export functionality and backups. 
In terms of equipment, the new server to come at Der Spiegel has been financially signed off and ordered. In the meantime, we focused our efforts to get the new TML collection processed, indexed and exported / imported from auxiliary machines to Neon. 


***

For more details, checkout the **weekly** highlights and release notes.

## Highlights
**28th Feb -> 6th Mar**
- Coco collection migration using the import/export functionality, to neon
- Bug fixes after the latest deploy hit Production
- Created database backups (cuz now we have backups 😁) to support collection migrations
- Opened snoop admin interface (task stats, etc) on :9990/snoop (next to grafana)

**6th - 13th Mar**
- After processing TML collection, different issues started to come up with annotations and OCR previews
- Spent the week troubleshooting unexpected behaviors with Nextcloud and Hypothesis
- Upgrade NEON with the latest improvements

**13th - 20th Mar**
- Still working on fixing a Hypothesis user sync, for multi-host set-ups
- Started upgrading Nextcloud to the latest version 16 and after, 17 as it was a bit outdated
- Also started indexing TML collection and OCR using Intella

**20th - 27th Mar**
- User sync, backups on multi-host environments
- Ongoing work on full system back-ups 

> ## Release notes 
> ### Snoop
>Date: Mar 25th / v0.7.6
>- create root documents only when migrating
>- also create document root on migratecollections
>- create empty blob directory when migrating collections
>
>Date: Mar 5th / v0.7.2 
>- fix typo in Collection.base_path
>- fixed issue with admin autologin
>- fixed issue where sync collections would stop processing of later
collections
>
>Date: Mar 4th / v0.7.0
>- auto-login into the admin interface
>- configure url prefix for all sites
>- fix admin interface for collections
>
>Date: Mar 1st / v0.6.0
>- one snoop for all collections
>
> ### Node
>Date: Mar 25th / v0.9.13
>- required: cluster >= 0.9.0, run as docker container called "cluster"
>- backups, "./liquid shell" and "dockerexec" now work in a multi-host environment
>
>Date: Mar 20th / v0.9.12
>- configure snoop's web server count and memory limit from
>  the [liquid]hoover_web_* variables
>- add [liquid]hoover_web_memory_limit
>- add [liquid]hoover_web_count
>- make hoover authproxy memory limit configurable
>
>Date: Mar 17th / v0.9.7
>- fix bug that blocked hypothesis embed in http
>- activate Nextcloud contacts app
>- add document preview to hoover ui
>
>Date: Mar 13th / v0.9.6
>- update dependencies and python for hoover,snoop,authproxy,core
>- fix user sync for hypothesis
>- fix setup script for Nextcloud
>
>Date: Mar 5th / v0.9.4
>- fixed issue with hoover collections getting set as public
>- fixed issue with sync collection blocking scheduling of others 
>- rename task groups to match tasks
>- bump search version
>- bump snoop version
>
>Date: Mar 1st / v0.9.0
>- unified snoop containers into single instance
>- backup and restore for collections