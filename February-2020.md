## Overview 
This month, we kept our priority of stabilizing and improving collection indexing process. The initial approach was to do that by changing Snoops' task management system. After intensive research, we could not find a third party solution that could magically fix all our problems, so we eventually focused on improving the internal task dispatching, currently used. Another feature to be deployed is automated importing/exporting a collection, from one machine to another. This comes in useful for the new Coconut collection, which was indexed on secondary machines like Rb and Xe, but needs to be moved on Neon, to be accessible for journalists.

February is also the last month (sadly! oh, so sadly!) we have Alex on the project 😢  

***

For more details, checkout the **weekly** highlights and release notes.

## Highlights
**1st -> 7th Feb**
- the new hardware from Bucharest office was plugged, set and is ready to play 
- went over the roadmap we agreed upon in Geneve and moved items up or down, according to current priorities 
- changing the task management system is still a first priority that is being researched / worked upon

**7th -> 14th Feb**
- new hardware got installed and seems to work great
- the Dev team had a technical planning around snoop processing optimizations, came up with a plan and started implementing it, with tasks such as:
 - Change database Task rows lock (select_for_update) to non-waiting;
 - Roughly limit queue size;
 - Simplify periodic dispatcher sequence;
 - Deactivated tesseract ocr pipeline from Tika;

**14th -> 21st**
- A new release was deployed with the latest indexing optimizations;  
- Xenon and Rubidium were cleaned, configured and got the latest code with Snoop patches and fixes;
- Coconut collection was successfully indexed on Rb;
- Continued with postgresql optimizations 
- Stability improvements for processing large collections
- Unifying Snoops' multi-collection into a single one / one database

**21st -> 28th**
- Importing / exporting collection feature was finalized
- Backup support was started
- Focus on collection migration to production

> ## Release notes 
> ### Snoop
>Date: Feb 26th
>
>Version 0.5.2
>- security updates
>- create index on initcollection
>
>Date: Feb 24th
>
>Version 0.5.1
>- fix bug with indexes being created twice
>- add subcommand to check if work is done
>
>Date: Feb 14th 
>
>Version 0.5.0:
>- merge periodic tasks into run_dispatcher every 30s
>- mark children of errored tasks as broken, not deferred
>- use priority queues in celery
> ### Node
>Date: Feb 28th
>
>Version 0.8.3
>- fix issue with archiving in-progress collection
>- add flags to skip backing up individual components
>
>Date: Feb 26th
>
>Version 0.8.2
>- add "backup" subcommand
>
>Date: Feb 14th
>
>Version 0.8.0:
>- disable Tika's tesseract integration
>- configured monitoring port for rabbitmq
>- use snoop 0.5.0 that supports limiting queue size; this upgrade requires the removal of all the rabbitmq >volumes under $liquid_volumes/collection/$name/rabbitmq.

