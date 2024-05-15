
#### Key Value store

- Stores information in the form of documents or pages so the data has a document and all information about that data is stored within that file
- These files can be in any format or structure and changes to one file does not affect the others
	- You can add more details to any of these documents without updating the others

#### ETCDCTL

- Command line client for ETCD 
- You can use it to store and retrieve key-value pairs
- To store a key value pair
	- ```./etcdctl set key1 value1```
	- For v3.0
		- ```./etcdctl put```
- To retrieve the stored data
	- ```./etcdctl get key1```
	- For v3.0
		- ```./etcdctl get```
		- 