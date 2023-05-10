https://minikube.sigs.k8s.io/docs/start/

![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/a5a8a1a7-6f42-4e3c-abae-4bd3e4c1b0c4)
```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

`minikube start`
![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/fa511f62-fde1-4dce-82fd-f80e8ca9ccd9)

`minikube kubectl -- get po -A`
![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/6dc17195-6a2d-4d0d-8a06-529525a85b44)

`minikube dashboard`
![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/c2678a17-d4f2-44f2-8104-c2504a3b8fd2)
![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/a293c5c6-1551-4364-b702-3c6cbe771270)

frontend.yml
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: frontend
  labels:
    app: frontend
spec:
  replicas: 3
  selector:
    matchLabels:
      app: frontend
  template:
    metadata:
      labels:
        app: frontend
    spec:
      containers:
      - name: frontend
        image: nikymn/wayshub-frontend-16
        stdin: true
        tty: true
        ports:
        - containerPort: 3000
```

frontend-svc.yml
```
apiVersion: v1
kind: Service
metadata:
  name: frontend
spec:
  type: NodePort
  selector:
    app: frontend
  ports:
    - protocol: TCP
      nodePort: 31000
      port: 3000
      targetPort: 3000
```

```
minikube kubectl -- create -f frontend.yml
minikube kubectl -- apply -f frontend-svc.yml
```

![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/b41228ce-31cf-49a8-9b0a-46993768a4f9)

```
minikube kubectl get all
```
![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/6a4d1f9f-b47b-401f-9857-3b6740c84a39)


```
minikube service frontend
```
![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/dece6dd0-9114-477f-a77e-0727b7190a8c)

![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/3f1d29ee-82b4-4c93-822b-d04ff9e1c8e0)
