#kind #secret #k8s #base64

```yml
apiVersion: v1  
kind: Secret  
metadata:  
  name: mongo-secret  
type: Opaque  
data:  
  username: YWRtaW4=  
  password: cGFzc3dvcmQ=
```

> [!INFO]
> - metadata/name - random name
 >- type Opaque - default for arbitary key-value pairs
> - data - key-value pairs
> - values must be base64 encoded
> - command for this: 
> `echo -n 'username' | base64` 