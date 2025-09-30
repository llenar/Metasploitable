## Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя nmap.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

* Какие сетевые службы в ней разрешены?
* Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
Приведите ответ в свободной форме.

## Ответ 1
Какие сетевые службы в ней разрешены?
<img width="967" height="635" alt="Screenshot_7" src="https://github.com/user-attachments/assets/aea8ecfc-cd75-4a1c-a0b2-87051cbd9d7a" />


Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)

1. vsftpd 2.3.4: [Backdoor Command Execution (Metasploit)](https://www.exploit-db.com/exploits/17491)
2. UnrealIRCd 3.2.8.1: [Backdoor Command Execution (Metasploit)](https://www.exploit-db.com/exploits/16922)
3. PostgreSQL 8.3.6: [Conversion Encoding Remote Denial of Service](https://www.exploit-db.com/exploits/32849)
4. PostgreSQL 8.3.6: [Low Cost Function Information Disclosure](https://www.exploit-db.com/exploits/32847)

## Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.

Запишите сеансы сканирования в Wireshark.

Ответьте на следующие вопросы:

Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?
Как отвечает сервер?

Приведите ответ в свободной форме.

## Ответ 2
Чем отличаются эти режимы сканирования с точки зрения сетевого трафика?

SYN - TCP [SYN]

<img width="778" height="664" alt="Screenshot_7" src="https://github.com/user-attachments/assets/2bb373d5-2993-4231-a5fb-c434dde3ef2f" />

FIN - TCP [FIN]

<img width="802" height="660" alt="Screenshot_1" src="https://github.com/user-attachments/assets/4a5c2fc0-d37d-48c1-a51b-f2512b04af81" />

Xmas - TCP [FIN, PSH, URG]

<img width="803" height="663" alt="Screenshot_2" src="https://github.com/user-attachments/assets/35533f85-d17f-427f-8f2c-87774521311e" />

UDP - TCP [FIN, PSH, URG]

<img width="716" height="356" alt="Screenshot_3" src="https://github.com/user-attachments/assets/1827a584-785e-4e9b-baf3-668558ecfc74" />


Как отвечает сервер?

SYN-сканирование:
- Открытые порты отвечают SYN-ACK.
- Закрытые — RST.

FIN-сканирование:
- Открытые — обычно не отвечают.
- Закрытые — RST.

Xmas-сканирование:
- Открытые — не отвечают.
- Закрытые — RST.

UDP-сканирование:
- Открытые — может не отвечать или отвечать, если есть специфичные службы.
- Закрытые — ICMP Port Unreachable.
