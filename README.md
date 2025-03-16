Чек-лист готовности к домашнему заданию

![Screenshot_15](https://github.com/user-attachments/assets/dbe19f03-e5f6-4c66-a87d-277e3a751f64)

![Screenshot_18](https://github.com/user-attachments/assets/7004b167-b488-4b35-8412-c48ba1bcd3ed)

Задание №1

1.После загрузки каталога src обезательно переносим файл .terraformrc в домашний каталог иначе инит не будет работать.

![Screenshot_1](https://github.com/user-attachments/assets/e82f1ba0-1af4-4d4e-800d-134973c870c1)

2.Файл personal.auto.tfvars является лучшим вариантом хранения паролей в виде переменных, согласно данному файлу .gitignore он игнорируеться.

3.Ответ HWXs9ODMTP5tw3om

![Screenshot_2](https://github.com/user-attachments/assets/44d7c7f8-1619-4982-945f-c0741118d086)

4.Первая ошибка отсутствует имя в обьявлении ресурса resource "docker_image" {

Вторая наименование ресурса не может начинаться с цифры 1nginx. 

Третья ошибка обращение к несуществующему  ресурсу name = "example_${random_password.random_string_FAKE.resulT}"

Четвертая ошибка буква в верхнем регистре в конце этой же строчки 

![Screenshot_3](https://github.com/user-attachments/assets/08889206-8538-4058-89a6-dd90002d5237)

Правельный код

terraform {
  required_providers {
    docker = {
      source  = "kreuzwerker/docker"
      version = "~> 3.0.1"
    }
  }
  required_version = ">=1.8.4" /*Многострочный комментарий.
 Требуемая версия terraform */
}
provider "docker" {}

#однострочный комментарий

resource "random_password" "random_string" {
  length      = 16
  special     = false
  min_upper   = 1
  min_lower   = 1
  min_numeric = 1
}

resource "docker_image" "nginx" {
  name         = "nginx:latest"
  keep_locally = true
}

resource "docker_container" "nginx" {
  image = docker_image.nginx.image_id
  name  = "example_${random_password.random_string.result}"

  ports {
    internal = 80
    external = 9090
  }
}

5.![Screenshot_4](https://github.com/user-attachments/assets/3d1ae04a-cdcd-497e-becc-56c0f0018ab1)

6.![Screenshot_5](https://github.com/user-attachments/assets/461fe7d8-0eb8-45fd-95cd-2540ba0c918e)

Ключ -auto-approve в Terraform автоматически подтверждает выполнение операций, которые требуют интерактивного подтверждения.Опасность в том что:

 Отсутствие проверки изменений

 Непреднамеренное удаление ресурсов

 Ошибки в конфигурации

 7.![Screenshot_6](https://github.com/user-attachments/assets/778b2e96-b485-4321-90a5-99b14356c01d)

 ![Screenshot_7](https://github.com/user-attachments/assets/abe688ea-93ae-46aa-87eb-31abf6f25a89)

 8.![Screenshot_8](https://github.com/user-attachments/assets/8e310320-3c69-415b-9f52-5330b83dedd5)

 Строчка keep_locally = true запрещает удалять образ в локальном хранилеще при операции дестрой 



