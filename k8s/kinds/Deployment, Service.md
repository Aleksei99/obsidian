#kind #k8s #depoloyment #service 

```yml
apiVersion: apps/v1  
kind: Deployment  
metadata:  
  name: mongo-deployment  
  labels:  
    app: mongo-deployment  
spec:  
  replicas: 1  
  selector:  
    matchLabels:  
      app: mongo-deployment  
  template:  
    metadata:  
      name: mongo-deployment  
      labels:  
        app: mongo-deployment  
    spec:  
      containers:  
        - name: mongo-deployment  
          image: mongo  
          imagePullPolicy: IfNotPresent  
          ports:  
            - containerPort: 27017  
          env:  
            - name: MONGO_INITDB_ROOT_USERNAME  
              valueFrom:  
                secretKeyRef:  
                  key: username  
                  name: mongo-secret  
            - name: MONGO_INITDB_ROOT_PASSWORD  
              valueFrom:  
                secretKeyRef:  
                  key: password  
                  name: mongo-secret  
      restartPolicy: Always  
---  
apiVersion: v1  
kind: Service  
metadata:  
  name: mongo-service  
spec:  
  selector:  
    app: mongo-deployment  
  ports:  
    - protocol: TCP  
      port: 27017  
      targetPort: 27017
```

> [!INFO]
> - selector: to connect to Pod through label
> - ports:
> 	- port: Service port
> 	- targetPort: container port of Deployment

```yml
apiVersion: v1  
kind: Service  
metadata:  
  name: mongo-express-service  
spec:  
  selector:  
    app: mongo-express  
  type: LoadBalancer  
  ports:  
    - port: 8081  
      protocol: TCP  
      targetPort: 8081  
      nodePort: 30000
```

> [!INFO]
> - type: LoadBalancer - assigns service an external IP address and so accepts external requests
> - nodePort: must beetween 30000-32767

> [!INFO]
> To assign public IP address to service use:
> `minikube service name_of_service`

