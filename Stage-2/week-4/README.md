Instalasi kubernetes disini saya mengikuti instruksi pada website `https://minikube.sigs.k8s.io/docs/start/`

![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/c870dfd0-ef7b-4b2f-aba1-6e1dca2af68f)

Jalankan minikube dengan command dibawah ini
```
minikube start
```

![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/fa511f62-fde1-4dce-82fd-f80e8ca9ccd9)

Lakukan verifikasi dengan membuat cluster baru dengan command
```
minikube kubectl -- get po -A`
```

![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/6dc17195-6a2d-4d0d-8a06-529525a85b44)

Bisa juga membuka dashboard minikube dengan command
```
minikube dashboard
```

![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/c2678a17-d4f2-44f2-8104-c2504a3b8fd2)

![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/a293c5c6-1551-4364-b702-3c6cbe771270)



Saya membuat file `frontend.yml` untuk membuat Multi-Node Cluster Frontend dari image `nikymn/wayshub-frontend-16`

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


Untuk deploy service saya membuat file `frontend-svc.yml` sesuai kebutuhan seperti name app, protocol, type port dan port

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

Selanjutnya saya menggunakan command dibawah ini untuk deploy aplikasi dari file `frontend.yml` dan `frontend-svc.yml`

```
minikube kubectl -- create -f frontend.yml
minikube kubectl -- apply -f frontend-svc.yml
```

![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/b41228ce-31cf-49a8-9b0a-46993768a4f9)

Untuk melihat informasi lengkap gunakan command dibawah ini

```
minikube kubectl get all
```

![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/6a4d1f9f-b47b-401f-9857-3b6740c84a39)

Jalankan service `frontend` dengan command dibawah ini

```
minikube service frontend
```


![image](https://github.com/nikymn/devops16-dw-nafis/assets/52950376/3f1d29ee-82b4-4c93-822b-d04ff9e1c8e0)
