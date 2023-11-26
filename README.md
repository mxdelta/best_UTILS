using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Привет, мир!");
    }
}


# Извлекает файлы из файлов 

binwalk -e king   

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

tar xf bak.out


