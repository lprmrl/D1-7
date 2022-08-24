# D1-7
Установка Terraform на хост
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform

Копируем проект с репозитория 
sudo git clone https://github.com/lprmrl/D1-7.git

Заходим в папку проекта 
cd D1-7

Для подключения к бующим серверам генерируем ключи
ssh-keygen

Редактируем variables.tf, необходимо изменить поля для Яндекс Облака :
sudo nano variables.tf
"token" - Инструкция тут https://cloud.yandex.ru/docs/iam/concepts/authorization/oauth-token
"folder_id" - Инструкция тут https://cloud.yandex.ru/docs/resource-manager/operations/folder/get-id
"cloud_id" - Инструкция тут https://cloud.yandex.ru/docs/resource-manager/operations/cloud/get-id

Для инициализации Terraform вводим команду
terraform init

Для проверки конфигурации Terraform вводим команду 
terraform plan

После успешной проверки конфигурации Terraform вводим команду для запуска
terraform apply

По завершению всех процессов в терминале отобразятся IP-адреса master и worker ноды
Apply complete! Resources: 8 added, 0 changed, 0 destroyed.

Outputs:

external_ip_address_manager = [
  [
    "xxx.xxx.xxx.xxx",
  ],
]
external_ip_address_worker = [
  [
    "xxx.xxx.xxx.xxx",
  ],
]
 
 Копируете любой из адресов и вставляете в браузер, открывается главная страница сайта.

