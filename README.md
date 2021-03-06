# Описание

Призванием проекта является блокировка большинства навязчивых рекламных и баннерных сетей, сетей сбора статистики, ботнетов и других вредоносных веб-ресурсов (Malware Domain List Hosts List), - с помощью файла `hosts`.

Свежая версия файла `hosts`: https://github.com/remotehelp/hosts


## Файл `hosts`

Файл `hosts` содержит в себе список основных вредоносных/рекламных хостов (adware + malware + tracking), которым сопоставлен несуществующий (ведущий в никуда, чёрную дырку ака blackhole, /dev/null IP) IP-адрес - это может быть либо `999.999.999.999` либо `127.0.0.0`, как в данном случае.

Почему именно `999.999.999.999` или `127.0.0.0`, а не `192.168.0.0` или `240.0.0.0`? Всё потому, что разные ОС, как и разные веб-браузеры, могут по разному реагировать на обращения к подобным IP-адресам  из текущих/существующих или зарезервированных сетей (IP-диапазонов), длительное время ожидая соединение, что может тормозить отображение веб-страниц браузером, - или вот например:

```
$ ping 999.999.999.999
ping: 999.999.999.999: Имя или служба не известны
$ ping 240.0.0.0
PING 240.0.0.0 (240.0.0.0) 56(84) bytes of data.
^C
--- 240.0.0.0 ping statistics ---
115 packets transmitted, 0 received, 100% packet loss, time 116715ms


$ ping 240.255.255.254
PING 240.255.255.254 (240.255.255.254) 56(84) bytes of data.
^C
--- 240.255.255.254 ping statistics ---
540 packets transmitted, 0 received, 100% packet loss, time 551917ms


$ ping 127.0.0.0
Do you want to ping broadcast? Then -b. If not, check your local firewall rules.


$ ping 999.999.999.999
ping: 999.999.999.999: Имя или служба не известны
```

Именно по-этому более православно будет, когда каждому из вредоносных хостов мы будем присваивать именно `999.999.999.999` или `127.0.0.0` вместо `192.168.0.0` или `240.0.0.0`.

### Как использовать файл `hosts`

Для использования достаточно заменить системный файл `hosts` в месте его размещения, в зависимости от оиспользуемой ОС, предлагаемым здесь файлом `hosts`, либо перекопировать его содержимое.
* [hosts - Википедия](https://ru.wikipedia.org/wiki/Hosts)
* [Reserved IP addresses - Wikipedia](https://en.wikipedia.org/wiki/Reserved_IP_addresses)


## Файл `hosts-dead`

Файл `hosts-dead` содержит список мёртвых вредоносных хостов, т.е. хостов, которым не присвое IP-адрес. Хосты перечисленные в этом файле время от времени проверяются и те, которые оживают снова заносятся/добавляются в файл `hosts`.

Для массовой проверки хостов используется прога `nslookup` путём проверки наличия в ответе на запрос поля `Name:`, в противном случае `nslookup` возвращает:

```
$ nslookup bla-bla-blu-ble-blah.com 8.8.8.8
Server:		8.8.8.8
Address:	8.8.8.8#53

** server can't find bla-bla-blu-ble-blah.com: NXDOMAIN
```


## Полезные ссылки

Далее представлен список полезных веб-ссылок, использовав информацию с которых можно обезопасить не только домашний ПК, но и веб-сервер. Например, для защиты веб-сервера можно использовать список вредоносных IP-адресов представляемых каждые 24 часа сайтов www.blocklist.de, - написать `bash-скрипт`, либо найти готовый, который регулярно (запускаемый по-крону) будет скачивать список IP-адресов и забивать их в правила файрвола/брандмауэра.

Некоторые из хостов по указанным ниже ссылкам уже могут быть занесены в наш вариант файла `hosts`.
* [MalwareDomainList.com Hosts List](http://www.malwaredomainlist.com/hostslist/hosts.txt)
* [EasyList](https://easylist.to/)
* [StevenBlack/hosts: Extending and consolidating hosts files from several well-curated sources ...](https://github.com/StevenBlack/hosts)
* [mitchellkrogza/Ultimate.Hosts.Blacklist](https://github.com/mitchellkrogza/Ultimate.Hosts.Blacklist)
* [www.blocklist.de -- Export all Attacker-IPs from the last 48 Hours.](http://www.blocklist.de/en/export.html)


## Обратная связь

Если сайт занесен в этот файл по ошибке или Вам известен новый вредоносный веб-ресурс, - пожалуйста сообщите нам!  Для обратной связи лучше всего используйте соответствующие разделы на github-e:
* [Issues](https://github.com/remotehelp/hosts/issues)
* [Pull requests](https://github.com/remotehelp/hosts/pulls)

Либо же:
* Сайт автора: www.remoteshaman.com | www.remoteshaman.ru | www.itmag.pro
* E-Mail для связи: www.remoteshaman.com [at] gmail.com
