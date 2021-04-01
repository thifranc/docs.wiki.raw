## Overview

The new server has finally arrived, so for the first couple of weeks, there was a lot of hardware set-up, configurations, migrations. This resulted in two new members of the family: Helium & Hydrogen 🍾. In parallel, in terms of features, OCR remains the top priority of the month.

***

For more details, checkout the **weekly** highlights and release notes.
## Highlights
**1st -> 8th May**
- Installed core OS to Helium & Hydrogen;
- Installed the cluster & Node; 
- Moved Hoover-inv on H and made it public;
- TML: processed the collection again, using H;
- Still struggling with OCR data - trying to match individual images from inside PDF;
- In progress: upgrade to Nextcloud 18 and Hypothesis backup and restore.

**9th -> 15th May**
- Worked on the OCR PDF results: split by files;
- Integrated Tesseract OCR into hoover;
- OCRed using Hydrogen for sample data and TML;
- Performed performance tests for the migration, results to which are documented [here](https://github.com/CRJI/EIC/wiki/Migrations-using-rsync-and-scp);
- Continuous work on Hypothesis Backup and Restore.

**16th -> 22nd May**
- Prepared the plan for the big migration to the new system;
- Started step 1 of the migration plan: copy the sources and blobs for collections from Neon to Helium;
- UI changes: collection processing progress and ETA under collection name;
- Progress on Tesseract OCR: processing whole PDF pages too;

**23rd -> 29th May**
- System migration to the new machine happened seamlessly with lower impact on prod env than anticipated
- Syncing of blobs, however, still ongoing

> ## Release notes 
> ### Snoop
>Date: May 28th / v0.9.3
>- run install and run pdf2pdfocr
>- index new boolean fields `ocrimage` and `ocrpdf` for each document
>- poll, cache and serve stats for each collection, in the /collections/ endpoint
>
>Date: May 13th / v0.9.0
>- unpack pdf images
>- run tesseract OCR as snoop task, initiated by the ocr_languages config
>- stop pasting ocr text entries over document text field
>
>Date: May 6th / v0.8.0 
>- remove ocr source path
>
> ### Node
>Date: May 15th / v0.9.18
>- add ocr_languages config to run tesseract OCR integrated with snoop
>- small UI changes related to OCR
>
>Date: May 6th / v0.9.17
>- fix issue with too many celery beat messages being sent
>- remove the path from ocr source in snoop, the path is now built from the source name: `$COLLECTIONS/$name/ocr/$source_name`
>


