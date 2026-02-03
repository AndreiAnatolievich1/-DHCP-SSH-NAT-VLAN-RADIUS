Настройка DHCP-сервера <br>

apt install isc-dhcp-server -y `устанавливаем программное обеспечение сервера` <br>

<img width="802" height="226" alt="Screenshot_1" src="https://github.com/user-attachments/assets/a386d5ea-4fdd-41e5-bfb7-342d35827560" /> <br>

#nano /etc/network/interfaces `переходим в конфигурационный файл интерфейсов` <br>

<img width="451" height="57" alt="Screenshot_2" src="https://github.com/user-attachments/assets/ca7a21e3-ffc5-4b2d-afb2-c050e65c513f" /> <br>

в файле <br>
`auto eth1` `обозначаем интерфейс, на котором наш сервер` <br>
`iface eth1 inet static` `указывает, что адрес наш статический` <br>
`address 192.168.4.2` `адрес самого сервера` <br>
`netmask 255.255.255.0` `маска сети` <br>
`gateway 192.168.4.1` `шлюза по умолчанию` <br>
`dns-nameservers 8.8.8.8` <br>

<img width="1143" height="320" alt="Без имени" src="https://github.com/user-attachments/assets/294d4303-e77a-41b8-b532-e8db39ada243" /> <br>

`#nano /etc/dhcp/dhcpd.conf` `переходим к конфигурационному файлу DHCP` <br>

<img width="751" height="652" alt="Screenshot_3" src="https://github.com/user-attachments/assets/9f6375fb-f589-4d3f-9892-6ed04a906d36" /> <br>

<img width="474" height="72" alt="Screenshot_4" src="https://github.com/user-attachments/assets/ad445118-632d-435d-bd67-f1f261baad1b" /> <br>
`#nano /etc/default/isc-dhcp-servers тут необходимо подключить интерфейс, с которым сервер будет принимать DHCP-запросы` <br>
 <img width="885" height="269" alt="Screenshot_5" src="https://github.com/user-attachments/assets/b34ad950-0ba9-4e03-bb1b-261b7604f783" />
