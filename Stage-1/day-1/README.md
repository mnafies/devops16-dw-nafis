Task A. DevOps

1. DevOps adalah Kombinasi dari DEVELOPMENT dan OPERATION yang bertugas sebagai penghubung antara divisi Development (Programmer) dan Operation (Infrastructure Server). Agar bisa beradaptasi dengan cepat terhadap pembaruan maupun perubahan suatu product dan serta menghilangkan hambatan Komunikasi antara tim Development dan Operation, sehingga pada saat Deployment nantinya akan lebih konsisten dan lancar.

2. lifecycle DevOps Plan : Proses perencanaan untuk seluruh alur kerja yang dibutuhkan sebelum developers mulai menulis kode program. Code : Proses ini merupakan tahap dimana developers mulai menulis kode yang dibutuhkan untuk membuat suatu produk. Build : Aplikasi yang sudah siap untuk masuk ke tahap pengujian, akan langsung di build supaya dapat mengetahui apakah kode tersebut masih terdapat error atau sudah layak masuk ke divisi tester.

=============================================================

Task B. Virtualization & Operating System

1. Hypervisor yaitu suatu program untuk membuat dan menjalankan virtual machine.

2. Operating System adalah penghubung antara software dan hardware agar dapat digunakan oleh pengguna. Dalam sebuah komputer ataupun server memerlukan minimal satu sistem operasi agar dapat digunakan untuk menjalankan suatu program.

=============================================================

Task C. VMware

![image](https://user-images.githubusercontent.com/52950376/224872876-a4d572b2-396e-46f1-ba31-17a17c67406e.png)
<br>Langkah pertama untuk membuat virtualization dengan vmware pilih ‘Create a New Virtual Machine’
<br>
![image](https://user-images.githubusercontent.com/52950376/224872941-488bad4a-05d9-4186-b5bc-aa9abeabff96.png)
<br>Lalu muat iso ubuntu yang sudah di download
<br>
![image](https://user-images.githubusercontent.com/52950376/224872974-9d02ce0a-9292-479f-8a47-075d2dc123d5.png)
<br>Pada bagian ini silahkan untuk menyesuaikan ukuran partisi hardisk yang akan digunakan dan pilih split virtual disk untu dynamic partition (tidak menggunakan local disk secara langsung)
<br>
![image](https://user-images.githubusercontent.com/52950376/224872990-57658129-bbf9-4091-ad15-4f75d7112deb.png)
<br>Kemudian pilih customize hardware untuk menyesuaikan kebutuhan seperti RAM, CPU ataupun Network adapter
<br>
![image](https://user-images.githubusercontent.com/52950376/224873020-ef06b2a8-62ed-430f-a39b-797ce003af5c.png)
<br>Pertama pilih install ubuntu server
<br>
![image](https://user-images.githubusercontent.com/52950376/224873043-76a945a8-01e9-4d12-a090-dd84e938862e.png)
<br>Bahasa English
<br>
![image](https://user-images.githubusercontent.com/52950376/224873077-3c53c628-2e4e-43bf-8729-988896e40605.png)
<br>Pada bagian ini bisa skip langsung DONE
<br>
![image](https://user-images.githubusercontent.com/52950376/224873146-c10aa9c7-17ea-4b57-a118-1b27a0f42ecf.png)
![image](https://user-images.githubusercontent.com/52950376/224873156-1c6ed2b3-72c4-4f8c-838f-ecedb7190662.png)
<br>Pada bagian network kita pilih manual untuk mengatur pada bagian IP Address
<br>
![image](https://user-images.githubusercontent.com/52950376/224873179-3275a2bf-1d80-4578-8235-20dc06440884.png)
<br>Silahkan untuk menyesuaikan dengan IP Address dan Gateway yang sedang terpakai pada local network, tentunya yang terhubung dengan internet
<br>
![image](https://user-images.githubusercontent.com/52950376/224873198-eeae2c5f-76fb-478e-9980-655146233adc.png)
![image](https://user-images.githubusercontent.com/52950376/224873204-c4544ba3-5bfc-4b2f-9f90-24a527b14221.png)
<br>Bagian ini bisa skip langsung DONE 
<br>
![image](https://user-images.githubusercontent.com/52950376/224873237-b52e11ac-7d36-4224-9a80-ba8edf6b2a58.png)
<br>Pilih Custom storage layout  
<br> 
![image](https://user-images.githubusercontent.com/52950376/224873282-a90b5821-5f3a-4d8c-9395-953838aafd65.png)
<br>Pada bagian partisi ini bisa untuk menyesuaikan sesuai kebutuhan terutama pada bagian SWAP yang berguna untuk virtual RAM pada OS linux. Pilih free space untuk membuat partisinya
<br>
![image](https://user-images.githubusercontent.com/52950376/224873303-0f84a90d-553b-4cfc-80d9-4a169d0f3f00.png)
![image](https://user-images.githubusercontent.com/52950376/224873312-653f9837-4dd8-460f-8b6a-a8fe49ec6792.png)
![image](https://user-images.githubusercontent.com/52950376/224873323-251fd912-8014-40f3-b0d6-cb304e49389b.png)
<br>kemudian pilih continue
<br>
![image](https://user-images.githubusercontent.com/52950376/224873358-99a07269-c9b3-4778-bbfd-0c24be57dc79.png)
<br>Bagian ini bisa di isi dengan lengkap, lalu jangan lupa untuk centak install openSSH untuk keperluan remote ubuntu melalui local network
<br>
![image](https://user-images.githubusercontent.com/52950376/224873374-9633c988-2a08-4fc9-bc78-016a5c850ab5.png)
<br>centang install openSSH 
<br>
![image](https://user-images.githubusercontent.com/52950376/224873418-14c16e6a-9e6c-4039-871c-1e129f77f80d.png)
<br>Setelah instalasi selesai pilih reboot now lalu unmount iso ubuntu yang terpasang
<br>
![image](https://user-images.githubusercontent.com/52950376/224873450-f1161585-fe63-4bda-9245-97b4f260b299.png)
<br>Login dengan username dan password yang sudah dibuat sebelumnya
<br>
![image](https://user-images.githubusercontent.com/52950376/224873492-f006f50b-322a-4c59-9d04-704f3f7b2e1b.png)
<br>Setelah berhasil untuk memastikan ubuntu sudah terkoneksi pada internet bisa masukan command ‘ping google.com’ lalu untuk mengakhiri silahkan tekan ctrl+c. Gambar dibawah ini sebagai contoh ubuntu sudah berhasil terkoneksi dengan internet
![image](https://user-images.githubusercontent.com/52950376/224873514-8d672201-75df-4301-ab0f-2e6494466581.png)
<br>
<br>Untuk remote ssh pada windows bisa menggunakan aplikasi remote ssh seperti telnet, xshell dan yang lainnya. Pastikan ubuntu pada vmware sedang dijalankan. Pada kali ini saya contohkan dengan menggunakan xshell 
![image](https://user-images.githubusercontent.com/52950376/224873562-ff92aa5b-39a4-45d3-bc82-24677f9eb363.png)
<br>Pilih icon yang sudah ditandai kotak merah untuk membuat sesi baru
![image](https://user-images.githubusercontent.com/52950376/224873578-ba49f9ad-25ef-4261-898e-5b3d5dd7745e.png)
<br>Isi sesuai denga nip yang sudah diatur pada ubuntu sebelumnya
<br>name : <sesuai kebutuhan>
<br>Host : <ip ubuntu>
<br>Port : 22
<br>Lalu pilih Connect atau OK
<br>
![image](https://user-images.githubusercontent.com/52950376/224873608-32f83324-3a6a-4e23-b9d1-6266dd0681d5.png)
<br>Pada bagian ini isi dengan username ubuntu
<br>
![image](https://user-images.githubusercontent.com/52950376/224873623-1a045a67-1934-4afa-95be-dd10e3278db5.png)
<br>Pada bagian ini isi dengan password ubuntu
<br>
![image](https://user-images.githubusercontent.com/52950376/224873644-cf4d6201-9a84-43b7-b1cd-fd3a760e367e.png)
<br>Gambar diatas merupakan contoh local pc sudah terkoneksi dengan ubuntu vmware
