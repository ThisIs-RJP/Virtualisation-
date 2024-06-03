
#### What are Secrets

- Secrets are used to store sensitive information like passwords or keys
	- Similar to ConfigMaps, only difference is they're stored in an encoded format

#### Two steps involved in working with Secrets

1. Create a secret
2. Inject it into the pod

#### How do you convert plain text to an encoded format?

- When storing data as secrets in a .yaml file, the secrets must be encoded

###### Answer encode "mysql"
```
echo -n "mysql" | base 64

Output
bXlzcWw
```

###### Note: You can also use a similar command to decode

```
echo -n "bxlzcWw" | base64 --decode
```


#### How to view secrets

- Run the command `kubectl get secrets`

#### Node on Secrets

- Secrets are NOT encrypted - they are encoded 
- Secrets are not encrypted in ETCD
	- Consider enabling encryption at rest 
- Anyone able to create pods/deployments in the same namespace can access the secrets
 