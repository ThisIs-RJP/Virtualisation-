
- It is good practice to have the definition files stored somewhere E.G GitHub
- The source code repository should be configured with the right backup solutions E.G GitHub  
- This means that even if you lose your entire cluster, you can redeploy your application on the cluster by simply applying these configuration files on them

#### But what if someone created an object imperatively

- A better approach to backing up resource configuration is to query the API server to save all resource configurations for all objects created on the cluster as a copy

#### Backup ECTD

- Remember that the ETCD server stores information about the state of the cluster
	- Info about the cluster itself, the nodes and every other resource created within the cluster are stored here
- You can backup the ETCD server itself
- You can get the location of where all the data was stored from configuring ETCD
	- You can specify this directory to be backed up 
- You can also take snapshots of the ECTD database by using the ETCD control utility snapshot save command

#### Restore the ETCD

- Stop the API server then run the ETCD snapshot command with the path set to the path of the backup file
- When you're done, reload the service daemon and restart the ETCD service