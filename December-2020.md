## Overview

December, even if it is the last month of the year, proves to be the most productive. We are re-writing the UI, bringing it to the 20's, we are building a new and most expected feature - the Tagging system - and supporting Mediapart: with them using their own Liquid Node, we can actually get direct feedback on user experience, bugs or crashes and fix and improve our product in the process in a faster pace. 

***

For more details, checkout the **weekly** highlights and release notes.

## Highlights
**28th November -> 4th December** 
- CI support, as VMS experienced crashes; 
- Production release of the fixes and updates done on the previous week;
- Continuing work on backend development of Tags;
  - Add/remove/edit tags;
  - Search by multiple tags;
- More snoop performance and bug fixes;
- Refactored all components to functions with hooks;
- Removed Redux and replaced by local states;
- UI for search by multiple fields - drag&drop chips;
- Server side data fetching for /whoami, /collections, /limits; 

**5th -> 11th December**
- Mediapart support for Hoover search;

> ## Release notes 
> ### Hoover UI
>Date: Dec 9th / v0.7.0 -> v0.7.4
>- remove cookie header overwrite;
>- pass headers to api;
>- add path part to API url;
>- get API url in SSR from environment variable;
>- items pagination in finder;
>
>Date: Dec 1st / v0.6.0
>- Redux refactoring
>
> ### Node
>Date: Dec 9th / v0.12.2 -> v0.12.3
>- breaking change! all data from the chat server is lost!;
>- update rocketchat and mongodb to latest version;
>- update hoover search: save user on first login;
>
>Date: Dec 8th / v0.11.7
>- fix rocketchat, codimd auth and autologout
>
>Date: Dec 6th / v0.11.6
>- update snoop: pagination - combine first/last page
>
>Date: Dec 4th / v0.11.4 -> v0.11.5
>- fix hoover search bug: couldn't search more than 21 collections
>- bug fixes for hoover UI
>  - fix OCR link in doc page
>  - fix Select All collections button
>- bug fixes and optimizations in snoop processing
>Date: Dec 1st / v0.11.3
>- update libraries for all django services;
>- snoop batch performance improvements;
>- only generate the secrets needed in the deployment; 
>
>Date: Nov 6th / v0.10.1
>- ui update with file browser
>- proxy the ui through nginx instead of static exports from the backend
>
> ### Snoop
>Date: Dec 11th / v0.13.0
>- don't update mime twice
>
>Date: Dec 1st -> Dec 10th / v0.12.1 -> v0.12.7
>- update dependencies;
>- add script to check running workers;
>- fix paginator when fetching last pages;
>- pagination of children: dirs first, then files;
>- combine last page of dirs with first of files;
>- fix download link and errored file resp;
>
