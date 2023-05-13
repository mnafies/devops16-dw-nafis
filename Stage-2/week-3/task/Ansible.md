Instalasi ansible dibutuhkan python pip, gunakan command dibawah ini untuk verifikasi python pada linux ubuntu
```
python3 -m pip -V
```
Jika python sudah ada selanjutnya menambahkan library ansible terlebih dahulu dengan command dibawah ini
```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py --user
```

![image](https://user-images.githubusercontent.com/52950376/236621563-c9d8f97a-7762-429c-bf13-ec9458eb02f8.png)

Selanjutnya instalasi ansible dengan command dibawah ini 
```
python3 -m pip install --user ansible
```

![image](https://user-images.githubusercontent.com/52950376/236621657-367dfc2f-0d77-479f-a98c-ebabaa874a36.png)

Setelah selesai lakukan verifikasi ansible dengan command dibawah ini
```
ansible --version
```

Jika verifikasi belum menunjukan adanya ansible bisa lakukan cara copy ansible ke directory `/usr/local/bin`

```
sudo cp .local/bin/ansible /usr/local/bin
```

![image](https://user-images.githubusercontent.com/52950376/236621717-24854864-d1be-4671-8d02-1cac9d22a563.png)

selanjutnya pada directory ansible saya membuat file 

- `ansible.cfg` untuk konfigurasi ansible 
- `Inventory` untuk data server
- `[name_file].yml` untuk konfigurasi ansible-playbook

kemudian gunakan perintah dibawah ini untuk menjalankan ansible playbook
```
ansible-playbook [name_file].yml
```

![image](https://user-images.githubusercontent.com/52950376/236625006-89df53e0-a0ae-40c6-ae36-3f99a8b47dfe.png)

`ansible.cfg`

```
[defaults]
inventory = Inventory
private_key_file = ~/.ssh/id_rsa
host_key_checking = false
interpreter_python = auto_silent
```

`Inventory`

```
[appserver]
103.49.239.40

[gateway]
103.139.193.91

[monitoring]
103.23.199.42

[all:vars]
ansible_user="devops"
ansible_pythone_interpreter=/usr/bin/python3
```
[add_user]

untuk password disini saya menggunakan metode enskripsi dengan menggunakan `whois`

![image](https://user-images.githubusercontent.com/52950376/236625768-86e4b7a3-bd00-486b-ba1a-483fb7f6355e.png)


- hosts : semua server

`adduser.yml`
```
- become: true
  gather_facts: false
  hosts: all      
  vars:
   - username: "devops"
   - password: "$5$65Cdft2l3J/LIY7d$evc4M4CzKfvO4Xaht8VW7qXd7e4nUUeJO9wDIUaIVk5" #Nafis111

  tasks:
    - name: "Creating User"
      ansible.builtin.user:
        groups: sudo
        name: "{{username}}"
        password: "{{password}}"
```
![image](https://user-images.githubusercontent.com/52950376/236627226-34ca326c-7af6-415b-babd-c10e78cdad0d.png)

![image](https://user-images.githubusercontent.com/52950376/236626350-925c44d0-f0aa-47dd-a60d-69f0f2d92c47.png)


- hosts : semua server

`install-docker.yml`
```
---
- hosts: all
  become: true
  vars:
    container_count: 4
    default_container_name: docker
    default_container_image: ubuntu
    default_container_command: sleep 1d

  tasks:
    - name: Install aptitude
      apt:
        name: aptitude
        state: latest
        update_cache: true

    - name: Install required system packages
      apt:
        pkg:
          - apt-transport-https
          - ca-certificates
          - curl
          - software-properties-common
          - python3-pip
          - virtualenv
          - python3-setuptools
        state: latest
        update_cache: true

    - name: Add Docker GPG apt Key
      apt_key:
        url: https://download.docker.com/linux/ubuntu/gpg
        state: present

    - name: Add Docker Repository
      apt_repository:
        repo: deb https://download.docker.com/linux/ubuntu focal stable
        state: present

    - name: Update apt and install docker-ce
      apt:
        name: docker-ce
        state: latest
        update_cache: true

    - name: Install Docker Module for Python
      pip:
        name: docker

    - name: add user docker group
      user:
        name: devops
        groups: docker
        append: yes
```
![image](https://user-images.githubusercontent.com/52950376/236627628-24ff8d21-e6c7-43d0-adf3-aa0f4f70c968.png)

![image](https://user-images.githubusercontent.com/52950376/236628588-647daf4e-ac04-46e7-853c-b85704b61ca0.png)

file `docker-compose.yml` untuk kebutuhan docker compose yang nantinya akan di copy melalui ansible
```
version: "3.8"
services:
   frontend:
    container_name: wayshub-fe
    image: nikymn/wayshub-frontend-16:latest
    stdin_open: true
    ports:
      - 3000:3000
```

#### [appserver]

- hosts : appserver

`wayshub-docker.yml`
```
- become: true
  gather_facts: false
  hosts: appserver
  tasks:
    - name: pull image
      docker_image:
       name: nikymn/wayshub-frontend-16:latest
       source: pull
    - name: copy docker compose
      copy:
        src: /home/server/ansible/config/docker-compose.yml
        dest: /home/devops
    - name: running docker compose
      command: docker compose up -d
```

![image](https://user-images.githubusercontent.com/52950376/236635544-ac9031a0-5093-4438-9702-288ab840aedc.png)

![image](https://user-images.githubusercontent.com/52950376/236635688-0c3d8cfa-d0dd-410e-a5de-4448c3c77bac.png)

![image](https://user-images.githubusercontent.com/52950376/236635613-b1a71b81-7ec5-4ff6-b8db-6fa5029d9e99.png)

#### [gateway]

file `rproxy.conf` untuk kebutuhan nginx yang nantinya akan di copy melalui ansible
```
server { 
    server_name node-exporter-app.nafis.studentdumbways.my.id; 
    
    location / { 
             proxy_pass http://103.49.239.40:9100;
    }
}
server { 
    server_name node-exporter-gate.nafis.studentdumbways.my.id; 
    
    location / { 
             proxy_pass http://103.139.193.91:9100
    }
}
server { 
    server_name prom.nafis.studentdumbways.my.id; 
    
    location / { 
             proxy_pass http://103.23.199.42:9090;
    }
}
server { 
    server_name dashboard.nafis.studentdumbways.my.id; 
    
    location / { 
             proxy_set_header Host dashboard.nafis.studentdumbways.my.id;
             proxy_pass http://103.23.199.42:3000;
    }
}
server { 
    server_name nafis.studentdumbways.my.id; 
    
    location / { 
             proxy_pass http://103.49.239.40:3000;
    }
}
```

- hosts : gateway

`install-nginx.yml`
```
---
- become: true
  gather_facts: false
  hosts: gateway
  tasks:
    - name: "Installing nginx"
      apt:
        name: nginx
        state: latest
        update_cache: yes
    - name: start nginx
      service:
        name: nginx
        state: started
    - name: copy rproxy.conf
      copy:
        src: /home/server/ansible/config/proxy/
        dest: /etc/nginx/sites-enabled
    - name: reload nginx
      service:
        name: nginx
        state: reloaded
```
![image](https://user-images.githubusercontent.com/52950376/236684969-9969d45f-f46b-4163-9544-a8001c726a2b.png)

![image](https://user-images.githubusercontent.com/52950376/236684984-121136f0-9e5e-46d2-972a-8c267150ad2d.png)

![image](https://user-images.githubusercontent.com/52950376/236681655-21944770-dae0-43c5-aca4-58def5d3b7ed.png)

![image](https://user-images.githubusercontent.com/52950376/236685070-b3d2da23-d716-498d-abf4-dabe21b9e42c.png)


