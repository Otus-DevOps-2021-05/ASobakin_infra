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

 




