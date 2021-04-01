## Overview

This month we virtually got together for a Roadmap Planning Session that concluded with what should be our focus for the next few months. However, before starting adding new features, we need to dig deeper into the UI technical debt, as we are missing the structure and stability to support anything new. For this, we need professional help: a developer with React / Next.js experience, that can understand what is there and do a major refactoring.
***

For more details, checkout the **weekly** highlights and release notes.

## Highlights
**3rd -> 16th October** 
- New oauth2, which was updated on all apps except Hypothesis;
- Starting from File browsing issues, started investigating UI infrastructure more in depth;
- Working on Drone CI;
- While working on translating components in container as non-root, investigating why celery is not working;

**17th -> 23 October**
- New proxy is merged into master: on Liquid 0.10+, you can download any size of file from Nextcloud;
- Research on the current UI structure and why it is behaving as it is; conclusion: it needs major refactoring;

**24th -> 30th October**
- Removed backend “hacks” from hoover UI;
- First meeting and onboarding with Mateusz Szczygielski;
- Progress on Nextcloud upgrade;

> ## Release notes 
> ### Node
>Date: Oct 22nd / v0.10.0
>- requires cluster v0.12.1
>- changed config files under [snoop], please check examples
>- use click for argument parsing (syntax changed, please check readme)
>- show app versions in home page
>- run snoop workers on every worker
>- set up nomad oversubscription
>


