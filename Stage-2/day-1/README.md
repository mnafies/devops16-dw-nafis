# Deploy Wayshub

#### Pertama, membuat vm pada idcloudhost dengan spesifikasi sebagai berikut
~~~
   - Appserver : 1 CPU, 2 GB RAM
   - Gateway : 1 CPU, 1 GB RAM
    Storage : 20 GB
~~~
![image](https://user-images.githubusercontent.com/52950376/230357155-ada5cfcc-cf50-4c28-b1cd-66708a0c6a6f.png)
![image](https://user-images.githubusercontent.com/52950376/230365328-57de95be-10a7-4edf-a3ba-ec302d0292d8.png)


## Konfigurasi pada server appserver
#### disini saya membuat directory bernama wayshub dan clone git frontend dan backend wayshub :
~~~
git clone https://github.com/dumbwaysdev/wayshub-frontend
~~~
~~~
git clone https://github.com/dumbwaysdev/wayshub-backend
~~~
![image](https://user-images.githubusercontent.com/52950376/230379636-4b9a2a79-572d-4649-a13b-b402da383542.png)

#### lalu melakukan instalasi node js versi 14
![image](https://user-images.githubusercontent.com/52950376/230380063-9c1d30b5-5e2c-4695-8047-2e6029a8c731.png)

#### setelah itu install module node js pada directory front end dan back end dengan perintah `nvm install` 
#### dan lalukan pengecekan pada browser client
![image](https://user-images.githubusercontent.com/52950376/230380525-74703f2e-97e8-4747-b31f-87326f76f25c.png) <br>
![image](https://user-images.githubusercontent.com/52950376/230382127-ea10cc08-0da0-43d0-a88d-6f9aa8a43da4.png)

~~~
front end : 103.189.235.157:3000
back end : 103.189.235.157:5000
~~~
![image](https://user-images.githubusercontent.com/52950376/230381528-5f59d281-c98d-46ce-b4ea-852668475421.png) <br>
![image](https://user-images.githubusercontent.com/52950376/230382202-30b1dbb5-ca30-445f-aab9-71c4f736551f.png) 


## Konfigurasi mysql
#### pertama lakukan instalasi mysql dengan perintah `sudo apt install mysql-server`
![image](https://user-images.githubusercontent.com/52950376/230384033-6da19adf-19ac-4633-bc30-4cb5a5ea1b53.png)


#### masuk akun root dengan perintah `sudo mysql -u root -p` untuk pembuatan user account dan memberi priviledge
![image](https://user-images.githubusercontent.com/52950376/230390386-cfd74766-27ad-4483-9d92-c12dfc3e9dc9.png)

#### pembuatan user 'nafis' dengan pssword 'nafis111'  dan memberi priviledge pada user 'nafis' dengan perintah
~~~
CREATE USER 'nafis'@'localhost' IDENTIFIED WITH mysql_native_password BY 'nafis111';
atau
CREATE USER 'nafis'@'%' IDENTIFIED BY 'nafis111';
~~~
~~~
GRANT ALL PRIVILEDGES ON *.* TO 'nafis'@'%' WITH GRANT OPTION;
~~~
![image](https://user-images.githubusercontent.com/52950376/230404464-a861d707-a2df-4ea6-a2d8-7db389ba2d1a.png) <br>
![image](https://user-images.githubusercontent.com/52950376/230406303-a6432081-26b7-4aa8-8337-a8e967d4e155.png)

#### selanjutnya melakukan setup password pada mysql dengan perintah `sudo mysql_secure_installation`
![image](https://user-images.githubusercontent.com/52950376/230390031-42bd2816-33cd-4856-9e1d-c7e78ca89269.png)

## pm2 ecosystem
![image](https://user-images.githubusercontent.com/52950376/230396944-05941d55-3f03-4e77-b1c1-db341d0345d3.png)
![image](https://user-images.githubusercontent.com/52950376/230397071-6d15f461-da40-4ed1-bf3e-21b55b9fac82.png)
![image](https://user-images.githubusercontent.com/52950376/230397501-8fc5188e-b715-43f6-a832-661f52fdaca3.png)

## Test dns
![image](https://user-images.githubusercontent.com/52950376/230397806-475ec8ab-9955-47de-8c7f-5f95bfb76833.png)
![image](https://user-images.githubusercontent.com/52950376/230397867-ebe1dd8e-df6e-487f-bc64-c1c293c4fba2.png)

## Integrasi frontend backend sql
![image](https://user-images.githubusercontent.com/52950376/230398626-5ce569c6-07e4-4c3a-bd4a-3a7b2f6639be.png)
![image](https://user-images.githubusercontent.com/52950376/230520935-1482a65b-bd33-42ff-a0f1-8d0c27b688da.png)
![image](https://user-images.githubusercontent.com/52950376/230399099-da23a3c2-c3b1-4706-b956-aef3942f6485.png)
![image](https://user-images.githubusercontent.com/52950376/230400280-e2077ee5-8353-4480-a402-d000dcf482e7.png)

## Backend to sql
![image](https://user-images.githubusercontent.com/52950376/230399989-642b4c3a-fdd8-4c15-8386-19275c22ed49.png)

## Membuat database sql
![image](https://user-images.githubusercontent.com/52950376/230406596-ff06ee8e-d732-4dfa-91bf-171950e558f0.png)

## Membuat database untuk backend
![image](https://user-images.githubusercontent.com/52950376/230407086-21642977-bfb8-45bd-ae9f-95f356deba97.png)
![image](https://user-images.githubusercontent.com/52950376/230407566-e2b4607e-49b5-4635-90bf-1e1cc4464ea2.png)
![image](https://user-images.githubusercontent.com/52950376/230407912-9095f41b-7d72-4cd0-bcd3-f34dacbc2a9d.png)
 

## Server gateway
![image](https://user-images.githubusercontent.com/52950376/230393676-bfaaa9fc-5d14-4e74-9759-f3f7e075d095.png)
![image](https://user-images.githubusercontent.com/52950376/230392856-f1a75abd-e5ce-4e59-85e6-06dce1b8e9a2.png)
![image](https://user-images.githubusercontent.com/52950376/230394429-1f006614-8f18-4d80-8a6b-d9edc187c7a2.png)
![image](https://user-images.githubusercontent.com/52950376/230395730-a9dfd4fd-069d-471d-be50-79227d722a8d.png)
![image](https://user-images.githubusercontent.com/52950376/230396086-e090dee4-fe0c-4420-9795-dc08635f2dfb.png)
![image](https://user-images.githubusercontent.com/52950376/230396275-0604e063-b5b3-44bb-95ce-7724a9d8b3a3.png)


## Test dengan buat user account wayshub
![image](https://user-images.githubusercontent.com/52950376/230408750-a683c116-e540-42b1-951f-63800aaf7c72.png)
![image](https://user-images.githubusercontent.com/52950376/230497575-b82387d2-f403-4a97-823b-a7db80305d8e.png)
![image](https://user-images.githubusercontent.com/52950376/230497692-6b49d4fd-0935-41ab-8890-9659fafe4d54.png)
![image](https://user-images.githubusercontent.com/52950376/230521236-452b7356-88de-40f8-aad1-5082999e2503.png)

