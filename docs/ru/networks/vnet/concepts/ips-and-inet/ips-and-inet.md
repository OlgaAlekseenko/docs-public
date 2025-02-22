## Сетевая адресация

При создании подсети задаются:

- имя подсети;
- адрес подсети;
- пул DHCP IP-адресов (даже если DHCP выключен для подсети);
- (опционально) статические маршруты в формате `<адрес подсети> - <next hop>`.

При этом действуют следующие правила:

1. Если для подсети включен DHCP, то в ней размещаются два DHCP-сервера, которые занимают первые два адреса из пула DHCP-адресов.

   Например, если для подсети `192.168.0.0/24` задан пул DHCP-адресов `192.168.0.11–192.168.0.254`, то DHCP-серверы будут использовать порты с адресами `192.168.0.11` и `192.168.0.12`.

1. Если к подсети подключен маршрутизатор с публичным адресом, то порту `SNAT` маршрутизатора будет назначен случайный адрес из оставшегося пула DHCP IP-адресов.

## Организация доступа в интернет

Чтобы маршрутизатор имел доступ в интернет, выберите опцию **Подключение к внешней сети** при его создании. При подключении сети к такому маршрутизатору выберите опцию **Доступ в интернет**.

Сетевые объекты, которым необходим маршрутизатор с доступом в интернет:

- VPN-туннель.
- Балансировщик нагрузки с доступом в интернет.
- Виртуальные машины с плавающими IP-адресами, подключенные к приватной сети за маршрутизатором.

  <info>

  Чтобы получить доступ к виртуальной машине из интернета, назначьте ей плавающий IP-адрес или подключите ее к внешней сети `ext-net` с публичными IP-адресами.

  </info>

  <warn>

  Назначение нового плавающего IP-адреса и выбор подсети из внешней сети происходит случайным образом.

  </warn>

## Пул публичных IP-адресов внешней сети ext-net

Во всех подсетях:

- DHCP выключен;
- используются DNS-серверы `5.61.237.120` и `5.61.237.127`.

<!-- prettier-ignore-start -->
| Имя подсети  | Адрес подсети    | Доступный для использования диапазон IP-адресов    | Шлюз            |
| ------------ | ---------------- | -------------------------------------------------- | --------------- |
| ext-subnet1  | 95.163.248.0/22  | 95.163.248.10—95.163.251.250                       | 95.163.251.254  |
| ext-subnet2  | 79.137.174.0/23  | 79.137.174.5—79.137.175.253                        | 79.137.175.254  |
| ext-subnet4  | 95.163.212.0/22  | 95.163.212.1—95.163.215.253                        | 95.163.215.254  |
| ext-subnet5  | 95.163.208.0/22  | 95.163.208.1—95.163.211.253                        | 95.163.211.254  |
| ext-subnet6  | 95.163.180.0/23  | 95.163.180.1—95.163.181.253                        | 95.163.181.254  |
| ext-subnet7  | 89.208.84.0/22   | 89.208.84.1—89.208.87.253                          | 89.208.87.254   |
| ext-subnet8  | 89.208.196.0/22  | 89.208.196.1—89.208.199.253                        | 89.208.199.254  |
| ext-subnet9  | 95.163.182.0/23  | 95.163.182.1—95.163.183.253                        | 95.163.183.254  |
| ext-subnet10 | 85.192.32.0/22   | 85.192.32.1—85.192.35.253                          | 85.192.35.254   |
| ext-subnet11 | 89.208.208.0/22  | 89.208.208.1—89.208.211.253                        | 89.208.211.254  |
| ext-subnet12 | 89.208.220.0/22  | 89.208.220.1—89.208.223.253                        | 89.208.223.254  |
| ext-subnet13 | 213.219.212.0/22 | 213.219.212.1—213.219.215.253                      | 213.219.215.254 |
| ext-subnet14 | 89.208.228.0/22  | 89.208.228.1—89.208.231.253                        | 89.208.231.254  |
| ext-subnet15 | 185.241.192.0/22 | 185.241.192.1—185.241.195.253                      | 185.241.195.254 |
| ext-subnet17 | 87.239.104.0/21  | 87.239.104.1—87.239.111.253                        | 87.239.111.254  |
| ext-subnet18 | 185.86.144.0/22  | 185.86.144.1—185.86.147.253                        | 185.86.147.254  |
| ext-subnet19 | 37.139.32.0/22   | 37.139.32.1—37.139.35.253                          | 37.139.35.254   |
| ext-subnet20 | 37.139.40.0/22   | 37.139.40.1—37.139.43.253                          | 37.139.43.254   |
| ext-subnet21 | 146.185.240.0/22 | 146.185.240.1—146.185.243.253                      | 146.185.243.254 |
| ext-subnet22 | 5.188.140.0/22   | 5.188.140.1—5.188.143.253                          | 5.188.143.254   |
| ext-subnet23 | 146.185.208.0/22 | 146.185.208.1—146.185.211.253                      | 146.185.211.254 |
| ext-subnet24 | 84.23.52.0/22    | 84.23.52.1—84.23.55.253                            | 84.23.55.254    |
| ext-subnet25 | 109.120.180.0/22 | 109.120.180.1—109.120.183.253                      | 109.120.183.254 |
| ext-subnet26 | 109.120.188.0/22 | 109.120.188.1—109.120.191.253                      | 109.120.191.254 |
| ext-subnet27 | 185.130.112.0/22 | 185.130.112.1—185.130.115.253                      | 185.130.115.254 |
| ext-subnet28 | 94.139.244.0/22  | 94.139.245.0—94.139.247.253                        | 94.139.247.254  |
| ext-subnet29 | 212.233.88.0/21  | 212.233.88.1—212.233.95.253                        | 212.233.95.254  |
<!-- prettier-ignore-end -->
