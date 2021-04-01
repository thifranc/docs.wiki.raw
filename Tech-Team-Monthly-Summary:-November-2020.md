## Overview

The focus of November is the UI technical debt. To help us overcome this tedious task, we started collaborating with Mateusz Szczygielski, which is doing a great job tackling issues one by one and getting us back on track with a user friendly, less buggy UI experience.
***

For more details, checkout the **weekly** highlights and release notes.

## Highlights
**1st -> 6th November** 
- Hoover UI style changes, fix scrollbars hidden behind header;
- file browser changes that were started a while back were merged and related bugs fixed;
- Jersey collection export + instructions 

**7th -> 13th November**
- More UI changes:
  - Pagination for locations and document files
  - Search shortcuts in e-mail and metadata
  - Search by metadata displayed as chips
  - More sorting options
  - Split document component file into independent sections components
  - Refactor document and doc components to use hooks from latest React

**14th -> 20th November**
- all systems have been rebooted and upgraded
- latest UI changes reached Production

**21st - 27th November**
- started the backend work for the tagging system;
- Small hoover/snoop/processing improvements (reduce log spam, adjust batch sizes);
- Refactor search page to use next.js fetching instead of redux;
  - implemented search page SSR;
- add redirect for raw files to new API;
- fixed empty email domain filter, missing fields not turning into search;

> ## Release notes 
> ### Hoover UI
>Date: Nov 13th / v0.5.0
>- Location and files pagination
>
>Date: Nov 5th / v0.4.0
>- new file structure navigation: finderjs file browser
>- update to nodejs 10
>
> ### Node
>Date: Nov 19th / v0.11.2
>- fix task group name for hypothesis-periodic
>- run tests for different apps at the same time
>
>Date: Nov 6th / v0.10.1
>- ui update with file browser
>- proxy the ui through nginx instead of static exports from the backend
>
> ### Snoop
>Date: Nov 5th / v0.12.0
>- pagination for doc children and locations
>- changed API for navigation
>