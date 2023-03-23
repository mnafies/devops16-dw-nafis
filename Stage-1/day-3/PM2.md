## PM2

##### install pm2 melalui npm dengan perintah `npm install pm2@latest -g`
<br>![image](https://user-images.githubusercontent.com/52950376/225348867-082f5663-b52c-4f1a-98e5-9fb91a244975.png)


##### jalankan nodejs melalui pm2 dengan perintah `pm2 start index.js`
<br>![image](https://user-images.githubusercontent.com/52950376/225350344-6b5c80c8-c883-4181-aeb9-6485f7e8ae16.png)

##### jalankan python melalui pm2 dengan perintah `pm2 start [nama file] --interpreter=python`
<br>![image](https://user-images.githubusercontent.com/52950376/225351240-7d416ae4-71e2-4100-a7c8-c020eae7cf0b.png)

##### gunakan perintah `pm2 ls` untuk monitoring
<br>![image](https://user-images.githubusercontent.com/52950376/225364149-a113846e-f672-4838-9e7b-a86628c956f5.png)


##### jika menemukan permasalahan dari status errored seperti gambar dibawah ini
<br>![image](https://user-images.githubusercontent.com/52950376/225364321-8a369fbd-3ade-4ea4-9792-313e42d01978.png)
##### bisa melakukan problem solving dengan melakukan pengecekan pm2 melalui perintah 'pm2 log'
<br>![image](https://user-images.githubusercontent.com/52950376/225364543-9cd981fc-b65c-404d-980d-52d41665895d.png)
##### seperti contoh gambar diatas untuk python mendapatkan status errored karena port 5000 sedang digunakan oleh aplikasi lain
##### solusinya bisa dimatikan dahulu dengan perintah `npx kill-port 3000`
##### lalu jalan kan kembali dengan perintah `pm2 restart [nama file]`
