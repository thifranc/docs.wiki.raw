## Adding and Removing collections

Adding, removing and modifying collections requires SSH access to the machine.

The administrator must place the collection files in a specific directory on the server, edit the configuration `.ini` file to add it, and redeploy the server to start processing it.

Specific instructions on managing collections can be found in
[the node documentation](https://github.com/liquidinvestigations/node/blob/master/docs/Hoover.md).

### Importing and Exporting collections

Collections can also be saved as zip files and restored by the administrator. This also requires SSH access to the machine.

Specific details for importing and exporting are [on the Maintenance wiki page](https://github.com/liquidinvestigations/docs/wiki/Maintenance#backup).

## Managing access rights

To change access rules to these collections, visit Hoover, click on the **ADMIN** button, and select **Collections**. There, each collection can be configured to allow users, groups or public access.

Please note: the *Public* checkbox allows any authenticated user to see the collection. It cannot be visited by unauthenticated users, so it is, in a sense, *Public to the server*.

For more details, follow
[the relevant Wiki article](https://github.com/liquidinvestigations/docs/wiki/Admin-Guide:-Permissions-for-Hoover-collections).

## Limitations

### Supported file types

Supported file types are listed [in this table](https://github.com/liquidinvestigations/hoover-snoop2/blob/master/docs/filetypes.md).

### Collection Size Limit

Collections are kept on a single SQL database each. This means we have a natural limit of how many files a collection can have.

Please keep each collection document count to **below 1 million documents**, and each collection data size **below 500 GB**.

For larger datasets, the admin must unpack/unarchive the data manually into folders, and split them up into collections based on the *1 million documents / 500 GB* limitations above. For ease of administering many collections, a user group can be created to allow access to many collections for many users in one go.

Please note that different types of data have a different density in number of files per TB. For example, zips tend to have the most files per TB, followed closely by emails (which are only a few KB each). Word documents, scans, pictures, and other multimedia tend to be less dense.  

Here are some rough examples on how one can reach the 1 million documents target:
- `10-20 GB`  - zips with emails (text only)
- `25-75 GB`  - emails (text only, unpacked)
- `100-300 GB` - emails (with attachments, unpacked)
- `25-150 GB` - zips with mixed content
- `200-500 GB` - Words, PDF, Scans, Pictures (unpacked)

Please use the rough estimation above to manually split the dataset into collections that are below the *1 million documents and 500 GB limit*. A good rule of thumb is to split datasets into collections of around `200-300 GB` each.

For example, if a dataset comes as a single 3 TB file called `data.zip`, the steps are:
- Manually extract the archive
- Check number of files and total size
  - File count in Linux: `find DATA_FOLDER -type f | wc -l`
  - Folder size in Linux: `du -hd1 DATA_FOLDER | sort -h`
- Splt extracted data into collections of around `200 GB` each, based on the examples above
  - Use `mv` commands to move folders around with no wait time, *on the same file system*
- If any file of size `> 200 GB` is found inside, unpack it manually and split its contents among more collections
- Final setup should have around 15 collections for that dataset