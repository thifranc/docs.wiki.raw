## Overview

The new system is finally up and running 🍾 
This month, our attention goes to migrating everything to the new system, using the resources for indexing and processing of new and old collections and stabilization. We need to make sure that everything runs smoothly for our users.
In June we are also recruiting ROSEDU's interns, which will join us for the summer.

***

For more details, checkout the **weekly** highlights and release notes.
## Highlights
**30th May -> 5th June**  
- Finalizing Hypothesis back up and restore task
- Struggling with Nextcloud 18 upgrade
- Finished sync-ing OCR data
- Finished blobs sync-ing

**6th -> 12th June**  
- TML processing got stuck on Helium; started to process it on Hydrogen, aiming to import/export the collection to production, while researching the issues faced on Helium;
- there is a new small addition to TML that needs to be indexed and processed;
- Updated Dokuwiki to 50.3

**13th -> 19th June** 
- Interviewed 6 students for ROSEDU summer internship program and picked our winners 
- processed TML using Hydrogen with 3rd & 4th batch indexed and OCRed and exported using the backup function

**20th -> 26th June**  
- working on running docker container as non-root;
- started work on an issue with password not updating for nextcloud and codimd db;
- Stephan on Vacation and Gabi not feeling that well, so not much else in between;

> ## Release notes 
> ### Snoop
>Date: June 4th / v0.9.6
>- paginate the queryset in retry_tasks
>- optimize tasks.retry_tasks through batch update
>- don't run pdf2pdfocr on files with a lot of text
>
> ### Node
>Date: June 4th / v0.9.19
>- hypothesis backup & restore
>- analyze pdfs with pdf2pdfocr
>
