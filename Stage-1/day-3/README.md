Task A. NodeJS

Instalasi NodeJS versi 10

<br>![image](https://user-images.githubusercontent.com/52950376/225331503-ee493d4a-c5ff-4ff1-9ef7-0b0558cde748.png)
<br>install nvm dengan perintah 'curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.38.0/install.sh | bash'
<br>
<br>![image](https://user-images.githubusercontent.com/52950376/225332197-e59510a2-080f-44a7-a36e-b7b07eaf73d1.png)
<br>gunakan perintah 'nvm use 10' untuk memakai nodejs versi 10


Deploy Dumpflix Frontend

<br>![image](https://user-images.githubusercontent.com/52950376/225335507-840432f3-680e-4ae5-b2b4-144c2b3fafc8.png)
<br>Pertama-tama clone git dumpflix frontend dengan perintah 
<br>'git clone https://github.com/dumbwaysdev/dumbflix-frontend'
<br>![image](https://user-images.githubusercontent.com/52950376/225336603-5a02d8e8-8015-4f5e-a532-405084034399.png)
<br>lalu tambahkan package nodejs pada directory dumpflix-frontend
<br>![image](https://user-images.githubusercontent.com/52950376/225337172-f96ba058-5002-4018-a1ea-b793e7877db0.png)
<br>selanjutnya jalankan npm dengan perintah 'npm start'
<br>
<br>lakukan pengecekan pada browser dengan memasukan url <ipserver:3000> contoh : 192.168.1.222:3000
<br>![image](https://user-images.githubusercontent.com/52950376/225338019-77cccbf3-9810-4e3f-a846-e52bf3603d11.png)

===============================================================

Task B. Golang

<br>Pertama-tama download dan install golang dengan perintah 'wget https://golang.org/dl/go1.16.5.linux-amd64.tar.gz && sudo su'
<br>![image](https://user-images.githubusercontent.com/52950376/225338980-cdb5645e-79fa-4ed1-b23e-d0a1f0b4d398.png)
<br>'rm -rf /usr/local/go && tar -C /usr/local -xzf go1.16.5.linux-amd64.tar.gz && exit'
<br>![image](https://user-images.githubusercontent.com/52950376/225340239-314c7c5f-1664-4517-b83b-b48f7ebaf331.png)
<br>
<br>kemudian masukan path go pada .bashrc
<br>'sudo nano .bashrc'
<br>
<br>![image](https://user-images.githubusercontent.com/52950376/225340926-0e782273-dc58-4437-9c38-e49ff2a90b47.png)
<br>masukan script 'export PATH=$PATH:/usr/local/go/bin'
<br>
<br>![image](https://user-images.githubusercontent.com/52950376/225341451-091aa825-2f4c-4b9f-a58a-5924778c96e9.png)
<br>
<br>buat nama file dengan perintah 'nano index.go'
<br>![image](https://user-images.githubusercontent.com/52950376/225341748-d5476706-c462-4fd8-8681-ef62d997e75c.png)
<br>
<br>buat script seperti contoh dibawah ini
<br>![image](https://user-images.githubusercontent.com/52950376/225342368-3220d1cd-c8a1-4709-a6b7-cf01ec8c4562.png)
<br>
<br>![image](https://user-images.githubusercontent.com/52950376/225342494-ff1cccb7-3474-4197-8642-5d6e20f24e1b.png)
<br>untuk menjalankan bisa dengan perintah 'go run index.go'

===============================================================

<br>Task C. Python
<br>
<br>![image](https://user-images.githubusercontent.com/52950376/225343750-7f796fdf-2b43-48a4-96df-5d36c3f0f5a8.png)
<br>Gunakan perintah 'python3 -V' untuk melihat versi python 

<br>![image](https://user-images.githubusercontent.com/52950376/225344119-eb096e19-e830-4104-8672-d7a1f874b168.png)
<br>Install package manager python3 dengan perintah 'sudo apt install python3-pip'

<br>![image](https://user-images.githubusercontent.com/52950376/225344719-65d9ae0a-816b-4f6a-a587-c444c817ddde.png)
<br>lalu install flash dengan perintah 'pip install flask'

<br>buat file index.py dengan perintah 'nano index.py' dan buat script dengan contoh dibawah ini
<br>![image](https://user-images.githubusercontent.com/52950376/225345060-970e9143-de49-437b-9b97-e44e874b0f01.png)
<br>![image](https://user-images.githubusercontent.com/52950376/225346478-c42724fe-5b4b-497b-b874-09496aa0968f.png)

<br>lalu jalankan dengan perintah 'python3 index.py'
<br>![image](https://user-images.githubusercontent.com/52950376/225346685-6cd68ed4-b5d9-4298-bdc9-61be923f9d0c.png)

<br>lakukan pengecekan pada browser client dengan url <ipserver:5000> contoh : 192.168.1.222:5000
<br>![image](https://user-images.githubusercontent.com/52950376/225346994-fef7ccd7-8007-4019-8e78-498bae39c291.png)


