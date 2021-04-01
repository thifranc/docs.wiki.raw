## Overview

April started in quarantine for everyone. It also started with system backups feature finalized: this crosses another improvement from the roadmap list and we are on to the next one: OCR tooling integration, which will be the focus of this month. In the meantime, we are invested in finding students from Poli to join the summer Internship program (same as last year).

Happy Easter! 🐰 

***

For more details, checkout the **weekly** highlights and release notes.

## Highlights
**27th Mar -> 3rd Apr**
- Nextcloud fixes (nextcloud url, https ciphers too old)
- Backup and restore for apps
  - Done for codimd, liquid-core, hoover-search, hoover-snoop, wiki
  - Not done for Hypothesis
  - Will not be done for Rocketchat and Nextcloud
- Upgrade production systems
- Migrating from mariadb to postgresql for Nextcloud
- Ongoing task: Intella's OCR export for TML

**3rd -> 15th Apr**
- Still struggling with Intella's OCR export for TML as it crashes on certain files
- Included some fixes for Backup & Restore functionalities

**15th -> 30th Apr**
- Manually tested backup & restore step by step which validated that the functionality works as intended
- Was not able to finalize the remaining 25% of TML's OCR export on Intella; decision is to focus more on the internal OCR solution, which is WIP, rather than troubleshooting Intellas limitations

> ## Release notes 
> ### Snoop
>Date: Apr 2nd / v0.7.7 
>- fix case when blob directory root is symlink
>
> ### Node
>Date: Apr 15th / v0.9.16
>- fix backup / restore for core
>
>Date: Apr 6th / v0.9.15
>- new subcomand "restore_apps"
>- the "backup" subcommand now backups apps too (without hypothesis)
>
>Date: Apr 2nd / v0.9.14
>- fix nextcloud login url in home page
>- fix issue with snoop not starting if a blob directory is a symlink
>- update https ciphers to ones recommended by mozilla
