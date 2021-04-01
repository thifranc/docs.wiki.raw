### Overview 

December started with a team meeting in Geneva (Dec 2nd - Dec 3rd). It was a great opportunity to catch up, talk about the latest events, our overall processes and where can we improve and, more important, what are we planning to do with our product that can bring added value and stability. 
We also had 2 guests that successfully installed our system following the documentation created by the team and validated everything is covered.

In terms of **direction and roadmap**, the most important decisions resulted from our planning session were:
 
- Spiegel: server migration & deployment for clustering together hoover inv and hoover work;
- Bucharest: build a staging server that will have a data set as big as necessary to have relevance in testing and validating new features, before deploying them to production;
- create backups to support a safe data migration between different machine
- move from Nomad, which proved so far to be buggy and limited and not exactly the best fit for our requirements to Kubernetes, which comes with the advantage of a higher adoption rate among the industry, so an experienced step further in front of competitors;
- Restores: restore a back-up in a freshly install liquid node;
- Get back to a single Snoop from the current multi-Snoop set-up (a single database instance);
- Implement Prefect: a new workflow management system, designed for modern infrastructure and powered by the open-source Prefect Core engine; this implementation will replace the internal task dispatching of Snoop, which is currently unreliable (sometimes it is necessary to retry tasks multiple times until all of them get processed).


***

For more details, checkout the **weekly** highlights and release notes.

**4th -> 16th Dec**
- started research on prerequisites for Kubernetes: Rancher;
- research and pick hardware components for the upcoming staging server;
- An end of the year deployment on neon, containing among other things:
 - Hypothesis cosmetic fixes
 - CodiMD authentication and cosmetic fixes 

**17th -> 23rd Dec**
- Focused on stabilizing the Demo environment by:
 - trying the new Nomad version;
 - Ansible config with wireguard and cluster;
- worked on fixing the indexing issues experienced with FL1;  
- A final year deploy was done on Staging and Production.

***

### 24th Dec -> 6th Jan: Happy Holidays! 
