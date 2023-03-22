Task A. Web Server

baik kali ini saya akan mencoba untuk menggunakan 2 VM seperti dibawah ini

![image](https://user-images.githubusercontent.com/52950376/226767979-c7e5cdc8-c6ee-431e-bc60-cd3f7537f6be.png)

pertama-tama saya jalankan nodejs melalui pm2 dengan perintah 'pm2 start npm -- start'

lalu saya akan membuat reverse proxy pada directory /etc/nginx/dumbways dengan script seperti dibawah ini

![image](https://user-images.githubusercontent.com/52950376/226771332-451539fc-9f35-496c-9e0c-633f3276fd01.png)

kemudian tambahkan script pada /etc/nginx/nginx.conf
![image](https://user-images.githubusercontent.com/52950376/226769811-d769ed2f-5bf2-40d0-a04e-34cc647959d2.png)

kemudian cek pada browser dengan ip server
![image](https://user-images.githubusercontent.com/52950376/226775572-3e52a08d-71b2-4041-8029-ccd7f8d1059b.png)


kemudian pada local host tambahkan pada conf 'sudo nano /etc/hosts' ip dan domain local server
![image](https://user-images.githubusercontent.com/52950376/226770354-79c37138-e742-497f-8d2c-046ad6b4785d.png)

kemudian untuk virtual domain edit hosts pada folder windows C:\Windows\System32\drivers\etc
![image](https://user-images.githubusercontent.com/52950376/226776161-47521fec-a8ad-44a1-bcbe-77fd80dc3fc8.png)

![image](https://user-images.githubusercontent.com/52950376/226776500-4cd6678d-7997-4c1d-8fd3-cc6cb935fc89.png)
