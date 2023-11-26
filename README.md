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


# маленький броузер

curl -s http://10.10.10.150/secret.txt | base64 -d

