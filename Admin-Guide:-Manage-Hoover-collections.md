Adding, removing and modifying collections requires SSH access to the machine. To change access rules to these collections follow
[the relevant Wiki article](https://github.com/liquidinvestigations/docs/wiki/Admin-Guide:-Permissions-for-Hoover-collections).

Instructions on managing collections can be found in
[the node documentation](https://github.com/liquidinvestigations/node/blob/master/docs/Hoover.md).

Supported file types are listed [in this table](https://github.com/liquidinvestigations/hoover-snoop2/blob/master/docs/filetypes.md).


## Collection Size Limit

Collections are kept on a single PostgreSQL database each. This means we have a natural limit of how many files a collection can have.

Please keep each collection size **below 1 million documents**, and total data size **below 1 TB**.

For larger datasets, the admin must unpack/unarchive the data manually into folders, and split them up into collections based on the limitations above.