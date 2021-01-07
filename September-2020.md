## Overview

We are back to business as usual. Our interns are doing a great job and started working on Liquid tasks, while we are focusing on collection processing related tasks, to serve the requests coming from journalists activity.
***

For more details, checkout the **weekly** highlights and release notes.

## Highlights
**5th -> 11th September** 
- Old, unused collection were set non-public (not visible) and back-ups were created for them: epstein; europarl-declarations; sillaro; albayrek 

**12th -> 18th September**
- Progress on Nextcloud 19 upgrade;
- Authproxy - successfully replaced by our intern Radu with oauth2-proxy with a custom provider;
- UI file browser - rebased and fixed by our intern Răzvan - works, but separate issues appeared on the subject;
- Changed user change from Dockerfile to docker-entrypoint;

**19th -> 25th September**
- Consul connect (fix for nextcloud multi-host); cluster now needs to run on host as root (no docker container).
Still to do: test migration (so we don’t lose db pass)
- Updating Dockerfile for newsleak to compile everything that docker build needs

**26th September -> 2nd October**
- Enabled sync on Nextcloud Uploads, which seemed to have been off for a while
- Processed Uploads collections;
- Improved processing performance by splitting the function type of the tasks and handling them separately;


> ## Release notes 
> ### Snoop
>Date: Sep 29th / v0.11.4
>- adjusted queue size limits
>
>Date: Sep 4th / v0.11.2
>- add "purge" subcommand
>- update dependencies
>