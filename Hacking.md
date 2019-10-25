## Debug mode
There is a global debug flag that enables debugging for all apps. This flag is **insecure** and should never be used in production.

1. Edit `liquid.ini` and set
    ```ini
    [liquid]
    debug = true
    ```
2. Run `./liquid deploy`

## Mount local repos
By default, `node` deploys a production cluster, with images from Docker Hub. For developemnt, it's useful to modify code locally and run it directly.

1. Clone all the relevant repositories by running `./repos/clone.sh`
2. Edit `liquid.ini` and set
    ```ini
    [liquid]
    mount_local_repos = true
    ```
3. Run `./liquid deploy`

Now all the apps will run using the locally cloned repositories in the `repos` folder.
