# Знакомство с облачной инфраструктурой и облачными сервисами (HW_5)


Дополнительное задание:

1. Выполните задание про подключение через бастион хост.(Исследовать способ подключения к someinternalhost в одну
команду из вашего рабочего устройства)
В сети Infra Развернуто 2 ВМ bastion (c публичным IP 178.154.225.93) и  someintrnalhost без публичного доступа (внутренний 10.130.0.29)
Предлагается воспользоваться командой ProxyCommand (https://rtfm.co.ua/ssh-podklyuchenie-v-privatnuyu-set-cherez-bastion-i-nemnogo-pro-multiplexing/)
Изменим файл ~/.ssh/config

Host 178.154.225.93
    User appuser
    IdentityFile  /home/asobakin/.ssh/asobakin_main_openssh
   


Host 10.130.0.29
    User appuser
    ProxyCommand ssh -W %h:%p  178.154.225.93
    IdentityFile  /home/asobakin/.ssh/asobakin_nomain

Конект ssh 10.130.0.29

Подключение прошло успешно.

2. Добавьте в ваш репозиторий Infra (ветка cloud-bastion):

   1. файл setupvpn.sh
   2. конфигурационный файл для подключения к VPN (переименуйте *.ovpn в cloud-bastion.ovpn)

3. Опишите в README.md и получившуюся конфигурацию и данные для подключения в следующем формате (формат важен для проверки!).

bastion_IP = 178.154.225.93
someinternalhost_IP = 10.130.0.29


4. Добавьте "Labels" cloud-bastion к вашему Pull Request


5.Для коннекта по VPN необходима установка iptables на ВМ YC.

# Основные сервисы Yandex Cloud  (HW_6)
testapp_IP = 178.154.224.197
testapp_port = 9292

Задание со звездочкой:
В команду созданий машины добавляется строчка `--metadata-from-file user-data=startupcloud.yaml`
Сам файл startupcloud.yaml в корне репозитория


# Модели управления инфраструктурой. Подготовка образов с помощью Packer(HW_7)
Изучены параметры PackerСоздан файл variables.json.examples с вымышленными значениями.Файл с реальными добавлен к .gitignore.
 
 # Знакомство с Terraform(HW_8)
Изучены параметры Terraform
Описана инфраструктура при помощи terraform и провайдера yandex. Выложен файл terraform.tfvars.example

# Основные компоненты terraform (HW_9)
Созданны два шаблона виртуальной машины: app.json и db.json
Созданные модули terraform: app and db
Созданы разные окружения с использованием модулей: stage and prod.

# Знакомство с Ansible (HW_10)
Теперь выполните ansible app -m command -a 'rm -rf ~/reddit' и проверьте еще раз выполнение плейбука. Что изменилось и почему? Добавьте информацию в README.md.

Во время первого запуска Ansible птыается достичь целевого состояния, но репа уже склоннирована (склонирована во время ручного запуска), после удаления повторный запуск приводит в  закрузке репозитария на машины.
 
