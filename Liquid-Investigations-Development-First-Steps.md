# Development First Steps #
## Install Cluster #
First you want to install the `cluster` following the [instructions here.](https://github.com/liquidinvestigations/cluster#quick-start) 

## Install Node #
Afterwards you should install `node`. The instructions can be found [here](https://github.com/liquidinvestigations/node#installation).

## Debugging jobs ##
In case you are running into any errors while setting up `node` and `cluster`, you can check `consul` (`http://10.66.60.1:8500/ui/dc1/services`) and `nomad` (`http://10.66.60.1:4646/ui/jobs`) for logs or error messages. In `nomad` you can click on the jobs name or ID following the links until you reach a page, where you can see the logs.

## Set up UI for local development ##
You might want to work on the Hoover UI, so you can set it up for local development as explained [here](https://github.com/liquidinvestigations/hoover-ui).

## Local Development ##
See [Development Readme](https://github.com/liquidinvestigations/node/blob/master/docs/Development.md) for instructions on how to mount the repos locally and set everything up for local development.

### Git Workflow ###
You want to create a feature-branch for everything you are working on. Once you need someone to review your work, push it to the remote repository, open a pull request and ask for review.

## Working on Hoover Snoop ##
If you are working on Snoop and want to debug running tasks or have a look at the databases, you can visit `http://10.66.60.1:9990/snoop/admin/_default/` (the IP adress depends on what you specified while setting up `cluster`). On the Snoop admin page you can see all the tasks and error messages appear there as well. Just choose a collection and go to `Tasks` for a list of tasks or `Task Stats` for an overview.

### Debugging in the shell ###
To debug tasks inside a shell you can use `./liquid shell hoover-workers:snoop-workers ./manage.py retrytask testdata 666 --fg` which will run the task in the foreground.

### Exploring the databases ###
To explore the databases you can enter `./liquid shell hoover-deps:snoop-pg psql -U snoop -d collection_testdata` and then use SQL. Enter `\h` for a list of SQL commands or `help` for a list of `psql` commands.

### Mange collections ###
See [Hoover Readme](https://github.com/liquidinvestigations/node/blob/master/docs/Hoover.md) for the insctructions on how to manage collections in hoover.
