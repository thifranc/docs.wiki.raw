### Overview

November was a month where system stability was affected by the storage hardware & configuration which could not keep up with Elastic Searches’ “resource hunger” on one side and the bundle of other apps that kept on crashing on the other and mixed with Internet speed issues that were pending a fix.
In depth performance analysis proved that the whole system needed improving in terms of storage and machine resource allocation to be able to keep up with users’ necessities. 

In this context, the focus of the team switched from building new features to:
 - system performance analysis;
 - stabilizing the latest features integrated: Hypothesis, CodiMD and OCR;
 - improving telemetry set-up and tools, which helped diagnose app crashes faster

Another important goal achieved in this period was building a documentation for:
 - App users 
 - Operators  / Partners that want to install and work with the full bundle 
 - Developers and newcomers that are helping on project development
 - Release process

Though it will be a WIP task, it is a big step further that is worth acknowledging.

***
  
For more details, checkout the **weekly** highlights and release notes.

**11th -> 17th Nov**
- Integrating OCR when indexing files from Nextcloud;
- Health check for Hypothsis workers;
- Upgrading Prometheus data persistence and memory;
- Documentation for: benchmarking process, upgrading process, security policy;

**18th - 24th Nov**
- The long awaited hardware upgrades started with Rb & Xe, the first QA two node cluster; 
- Demo environment proved to be a little disaster magnet, with Hetzner server misconfiguration identified a bit late and a buggy Nomad 0.10 version that added to the list of issues;
- Deployment on Neon that proved to be a difficult task due to all the configurations required;
- The aftermath: search working disruptively slow and overall system stability affected;

**25th - 30th Nov**
- Due to production migrations and deployments, this weeks' focus is to get the system back on its feet and stable; 
- Elastic Search's storage limitations still keeps the overall usability of search under decent parameters to a minimum;
- Hoover ES and PG data migrations were performed, causing production downtime; 
- In terms of apps functionalities: the much anticipated cosmetic fixes for Hypothesis were done; CodiMD wasn't as lucky - still causing issues and it is not stable, which opens the conversation of finding alternative solutions for annotations.


  

