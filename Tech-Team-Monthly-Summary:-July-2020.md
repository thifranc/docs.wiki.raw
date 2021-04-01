## Overview

July kicked off the summer internship program, with two students joining our team for a couple of months 📚. 
They will start their internship by reading a looot of documentation, with a few practical assignments, an [onboarding curriculum](https://hackmd.io/upSx7g7qSYSjE0poRtprkQ) put together by Gaby that will prep them for some Liquid action.
On the Liquid side, most of the month was focused on transferring FL & PT collections on Helium (neon).

***

For more details, checkout the **weekly** highlights and release notes.
## Highlights
**27th June -> 3rd July**  
- kicked off the internship program: set-up a project board for our students, created an introductory program for the first month, focusing on documentation for technologies used by our system; organized them in an Agile framework: daily syncs, 2 week sprints;
- On the product side, still encountering processing errors and FL and TML OCR results are pending availability on production. Still working on identifying errors stabilizing the process.

**4th -> 10th July**  
- database errors caused by miss-configurations have been identified and fixed;
- production system upgraded;

**11th -> 17th July**
- FL/PT collections were transferred on Hydrogen and to start processing, which took a few days;
- Started backup for the collections

**18th -> 24th July**
- Processing for the collections is still ongoing;
- Identified, investigated and fixed some db issues on Demo, which caused 502 errors;   

**25th - 31st July**
- tml, tml2 and fl27 finalized indexing; fl28 & fl29 encountered errors that stopped indexing so restarting the process;
- Staging ops: retry and backup for all collections


> ## Release notes 
> ### Snoop
>Date: July 30th / v0.11.1
>- set time and memory limits for each task
>- set variable workers for each host
>
>Date: July 10th / v0.10.3
>- pdf2pdfocr: manually close and delete the tmpfile
>
>Date: July 5th / v0.10.2
>- split periodic tasks: run_dispatcher, save_stats
>- fixup saving stats
>- each rabbitmq queue now holds all tasks for a single collection
>- every snoop process that runs the dispatcher must now configure SNOOP_RABBITMQ_HTTP_URL as commented in the settings file
>- Tasks that are BROKEN or ERROR will be retried every 10 days
>
>Date: July 3rd / v0.9.7
>- fix queueing; fix new style checks
>
>Date: June 4th / v0.9.6
>- paginate the queryset in retry_tasks
>- optimize tasks.retry_tasks through batch update
>- don't run pdf2pdfocr on files with a lot of text
>
> ### Node
>Date: July 6th / v0.9.22
>- update snoop to v0.10, now scheduling each collection separately
>- safe to delete $volumes/snoop/rabbitmq when upgrading
>Date: July 3rd / v0.9.21
>- fix snoop task queueing
>- don't run celery beat with zero workers
>
>Date: July 2nd / v0.9.20
>- add new config [liquid]http_protocol_override
>- allow selecting collections to be backed up through new command-line argument
>- update apps: CI, codimd, dokuwiki, some Python services
>- ensure it all runs as a tor hs
>