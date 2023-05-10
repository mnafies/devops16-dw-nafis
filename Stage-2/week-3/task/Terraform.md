
Instalasi terraform dengan script dibawah ini

```
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```

![image](https://user-images.githubusercontent.com/52950376/236508484-8da8ff8c-fc65-4f84-8db2-6e47405d9c21.png)

Verifikasi dengan command 
```
terraform
```
![image](https://user-images.githubusercontent.com/52950376/236508663-6da391aa-b1d4-482f-bb98-a7589dde6769.png)

kemudian saya membuat folder dan file `main.tf` untuk configurasi terraform

![image](https://user-images.githubusercontent.com/52950376/236513027-81e557e6-ae2d-4ab9-87d9-f50f0cf7ffe5.png)

di dalamnya berisikan konfigurasi detail server idch seperti dibawah ini

```
terraform {
  required_providers {
    idcloudhost = {
      source = "bapung/idcloudhost"
      version = "0.1.2"
    }
  }
}

provider "idcloudhost" {
    auth_token = "" # API Token from idcloudhost.com
    region = "jkt01"
}

resource "idcloudhost_vm" "nafis-appserver" {
    name = "nafis-appserver"
    os_name = "ubuntu"
    os_version= "20.04"
    disks = 20
    vcpu = 1
    memory = 1024
    username = "nafis"
    initial_password = "Katasand1" # Combination of Uppercase, Lowercase & Numbers
    billing_account_id =  # Billing ID from idcloudhost.com
    public_key = "ssh-rsa xxxxx server@server"
    backup = false
}

resource "idcloudhost_vm" "nafis-gateway" {
    name = "nafis-gateway"
    os_name = "ubuntu"
    os_version= "20.04"
    disks = 20
    vcpu = 1
    memory = 1024
    username = "nafis"
    initial_password = "Katasand1" # Combination of Uppercase, Lowercase & Numbers
    billing_account_id =  # Billing ID from idcloudhost.com
    public_key = "ssh-rsa xxxxx server@server"
    backup = false
}

resource "idcloudhost_vm" "nafis-monitoring" {
    name = "nafis-monitoring"
    os_name = "ubuntu"
    os_version= "20.04"
    disks = 20
    vcpu = 2
    memory = 2048
    username = "nafis"
    initial_password = "Katasand1" # Combination of Uppercase, Lowercase & Numbers
    billing_account_id =  # Billing ID from idcloudhost.com
    public_key = "ssh-rsa xxxxx server@server"
    backup = false
}

resource "idcloudhost_floating_ip" "ip-appserver" {
    name = "nafis-appserver"
    billing_account_id =  # Billing ID from idcloudhost.com
    assigned_to = idcloudhost_vm.nafis-appserver.id
}

resource "idcloudhost_floating_ip" "ip-gateway" {
    name = "nafis-gateway"
    billing_account_id =  # Billing ID from idcloudhost.com
    assigned_to = idcloudhost_vm.nafis-gateway.id
}

resource "idcloudhost_floating_ip" "ip-monitoring" {
    name = "nafis-monitoring"
    billing_account_id =  # Billing ID from idcloudhost.com
    assigned_to = idcloudhost_vm.nafis-monitoring.id
}
```

setelah membuat file `main.tf` gunakan command dibawah ini untuk insiasi terraform
```
terraform init
```

![image](https://user-images.githubusercontent.com/52950376/236516100-5283a012-5479-4a64-9e61-7751f024bd3a.png)

setelah itu gunakan command dibawah ini untuk menjalakan terraform dengan konfigurasi yang sudah ada
```
terraform apply
```
![image](https://user-images.githubusercontent.com/52950376/236623514-e6ee0d5a-b95a-4220-91d8-08de4fb8aacd.png)

![image](https://user-images.githubusercontent.com/52950376/236623532-c8a50e79-04f8-4444-8333-d61e4e73a665.png)

![image](https://user-images.githubusercontent.com/52950376/236623542-9e59ed3a-9704-4535-b6cf-496cf903cdf7.png)

![image](https://user-images.githubusercontent.com/52950376/236516503-9ed55cd1-658b-41f3-81c6-3e1c051c05e5.png)

![image](https://user-images.githubusercontent.com/52950376/236517119-69d07128-2485-49e6-9dd2-fa2c1abb1dc2.png)

Server sudah terbuat pada idch

##### appserver

![image](https://user-images.githubusercontent.com/52950376/236517245-9a22eff1-759e-4199-a815-ffc6b993792b.png)

##### gateway

![image](https://user-images.githubusercontent.com/52950376/236517365-88507654-67b7-4c7d-ae42-91028e541da7.png)

##### monitoring

![image](https://user-images.githubusercontent.com/52950376/236517470-bc01ae0e-ff59-4b33-b6a4-bc83492ab5d8.png)




