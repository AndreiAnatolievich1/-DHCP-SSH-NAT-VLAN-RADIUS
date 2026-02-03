`switch0> en` <br>
`switch0# conf t` <br>
`switch0(config)#hostname switch2` <br>
`switch2(config)# enable secret Tomil321` **задаём пароль на enable** <br>
`switch2(config)# service password-encryption ` <br>
`switch2(config)#vlan 2` <br>
`switch2(config-vlan)# name user` <br>
`switch2(config-vlan)# ex` <br>
`switch2(config)#vlan 3` <br>
`switch2(config-vlan)# name guest` <br>
`switch2(config-vlan)# ex` <br>
`switch2(config)#vlan 4` <br>
`switch2(config-vlan)# name server` <br>
`switch2(config-vlan)# ex` <br>
`switch2(config)#vlan 5` <br>
`switch2(config-vlan)# name switch1` <br>
`switch2(config-vlan)# ex` <br>
`switch2(config)#int vlan 5`  <br>
`switch2(config-if)#ip address 192.168.5.3 255.255.255.252` **Задаем ip на интерфейс коммутатора для удаленного подключения** <br>
`switch2(config-if)# ip default-gateway 192.168.5.1` **задаем шлюз по умолчанию** <br>
`switch2(config-if)# ex` <br>
`switch2(config)#int range f0/1-2` **переходим к настройке нескольких интерфейсов** <br>
`switch2(config-if-range)#switchport mode access` **указываем что данный интерфейс является интерфейсом доступа** <br>
`switch2(config-if-range)#switchport access vlan 2 ` **указываем vlan этого интерфейса** <br>
`switch2(config-if-range)#ex`  <br>
`switch2(config)#int range f0/3-4 `<br>
`switch2(config-if-range)#switchport mode access ` **указываем что данный интерфейс является интерфейсом доступа** <br>
`switch2(config-if)#switchport access vlan 3 ` **указываем vlan этого интерфейса** <br>
`switch2(config-if-range)#ex`  <br>
`switch2(config)#int f0/10` <br>
`switch2(config-if)#switchport mode trunk` **обозначаем интерфейс как trunk , это озночает что по нему теперь могут ходить тегированные frame** <br>
`switch2(config-if)#switchport trunk all vlan 2,3,4,5`  <br>
`switch2(config-if)#ex` <br>
`switch2(config)# username admin_sw2 privilege 15 secret Pa$$w0rd21` **задаём пользователя с правами admina** <br>
`switch2(config)# line console 0` **переходим в режим настройки консольного подключения** <br>
`switch2(config-line)# login local` **nребование аутентификации по локальной базе пользователей при подключении через консоль** <br>
`switch2(config-line)#en` <br>
`switch2(config)# line vty 0 15` **Переход в режим настройки виртуальных терминальных линий (VTY) с 0 по 15. Эти линии используются для удаленного доступа (Telnet/SSH).** <br>
`switch2(config-line)# login local` <br>
`switch2(config-line)# transport input ssh` **Разрешение только SSH подключений на VTY линиях** <br>
`switch2(config-line)# login authentication default` <br>
`switch2(config-line)# en` <br>
`switch2(config)#ip domain-name test1.local ` **Установка доменного имени для устройства. Это необходимо для генерации RSA ключей, которые используются в SSH**<br>
`switch2(config)#crypto key generate rsa general-keys modulus 2048 ` **Генерируем ключи шифрования** <br>
`switch2(config)#aaa new-model` <br>
`switch2(config)#radius-server host 192.168.4.2 auth-port 1645` <br>
`switch2(config)#radius-server key DerParol21` <br>
`switch2(config)#aaa authentication login default group radius` <br>
`switch2(config)#aaa authorization exec default local group radius local` <br>
`switch2(config)#aaa accounting exec default start-stop group radius` <br>
