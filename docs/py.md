## Встроенные "фишки"

```python
str_a = '[3,4,5,6,7]'
list_a = eval(str_a) # Преобразует строку в список в данном примере

str_b = "{'str': 'string', 'list': [1,5,7,9], 'int': 6}"
dict_b = eval(str_b) # Преобразует строку в словарь в данном примере

for i, x in enumerate(list_a): # В перебераемых объектах, так же дает итератор!
    print(i, x)
for k, v in dict_b.items(): # Перебор словаря ключ:значение
    print(k, v)
```

## Списки
```python
lst = [1,2,3,4]
el = lst.pop() # Удаляет последний элемент и возвращает его (el = 4)
string = ' '.join(map(str, lst)) 
# map - применение любой функции ко всем элементам. в этом примере функция str
# .join собирает список в стоку с указанным разделителем
lst.append(string) # Добавляет элемент в конец списка
```

## Строки
```python
string = ' Какая то стока '
string.strip() # обрезает пробельные символы с начала и конца
string.replace('а', 'j') # замена, заменяет все совпадения. 3 арг можно указать сколько совпадений заменить
string.lower() # переводит всю строку в сточный формат
string.upper() #  переводит всю строку в прописной формат
string.split(' ') # разбить строку в список по разделителю
string.title() # каждое слово с большой буквы
```

## Работа с файлами
```python
path = r'dir\dir\file.txt' # путь к файлу
wr_data = 'Строка для записи в файл'
# открыть файл r - для чтения, w - для записи, a - дозаписать, b - двоичный формат
with open(path, 'r', encoding='utf8') as f: 
    data_str = f.read() # прочитать весь файл
    f.write(wr_data) # записать в файл
    data_lst1 = f.readlines() # возвращает список строк
    data_lst2 = f.read().split('\n') # возвращает список строк
```

## Время и дата
```python
from datetime import datetime, timedelta, date
import time

time.sleep(3) # пауза выполнения скрипта
d1 = datetime.now() # получить сегодняшнюю дату и время
d2 = date.today() # получить сегодняшнюю дату 
d1.year # год
d1.month # месяц
d1.day # день
d1.hour # часы
d1.minute # минуты
datetime.strptime(str(d2), '%Y-%m-%d').strftime('%b %d, %Y') # сменить формат даты
```

## Работа с OS
```python
import os
import shutil

path1 = r'dir\file.txt'
path2 = r'dir\dir\file.txt'
os.replace(path1, path2) # Переместить файл
name_format = os.path.basename(path1) # имя файла с разширением
os.listdir('dir') # получить список файлов и папок
path1.endswith('.txt') # вернет True если файл txt
os.path.splitext(name_format)[0] # имя без разширения
os.path.splitext(name_format)[1] # формат без имени
os.makedirs('dir\\dir\\dir') # создать папку
os.remove(path1) # удалить файл
os.rmdir('dir') # удалить папку если она пустая
os.path.exists(path1) # проверяет есть ли файл
os.path.abspath('1.jpg') # возвращает абсолютный путь
os.stat(path).st_size # возвращает количество байт файла
shutil.rmtree(path1) # удалить папку со всем содержимым
```

## Работа с FTP
```python
import ftplib

host = '127.0.0.1'
login = 'username'
password = 'password'
path1 = 'dir\\file.txt'
path2 = 'dir\\image.jpg'
f_name1 = 'file.txt'
f_name2 = 'file.txt'
ftp = ftplib.FTP(host, login, password) # создаем ФТП
ftp.cwd('/uploads/imgs/') # переход в папку
ftp_dirs = ftp.nlst() # список файлов и папок
ftp.mkd('dir_name') # создать папку
# загрузка файлов. в режиме открытия файла rb
ftp.storlines(f'STOR {f_name1}', path1) # загрузка txt файла (имя, путь)
ftp.storbinary(f'STOR {f_name1}', path1, 1024) # загрузка других файлов (имя, путь, байты)
ftp.quit() # закрыть соединение
```

## Регулярки
```python
import re

string = 'Какой то текст Какой то текст'
result1 = re.search('то', string) # вернет объект с первый совпадением
result1.group(0) # строка найденного (то)
result2 = re.findall('то', string) # вернет список всего найденного
result3 = re.sub('то', 'ТА', string) # замена в строке
reg = re.compile('то') # создает объект с регулярным выражением для дальнейшего использования
reg.search(string) # тоже что и re.search('то', string)
```

## Запросы requests
Это сторонняя библиотека. Требует установки.
Оф документация: [https://pypi.org/project/requests/](https://pypi.org/project/requests/)

    pip install requests

```python
import requests

url ='https://google.com'
getinfo = requests.get(url) # простой запрос страницы получаем объект
text = getinfo.text # код страницы
json = getinfo.json() # преобразует json ответ в словарь
content = getinfo.content # содержание в двоичной системе. нужен для сохранения файла
post = requests.post(url) # пост запрос без параметров.
# в качестве параметров можно отправлять data=data, json=json (фотмат dict) и другие параметры
ses = requests.Session() # создает объект сессии
ses.headers.update({"Content-Type": "application/json"}) # редактирование заголовков в dict формате
ses.cookies.update({'key':'value'}) # обновление куков в dict формате

# ниже пример загрузки файла на сервер с дополнительными параметрами
with open('1.mp4', 'rb') as f:
    file ={
        'file':('1.mp4', f),
        'ajax':(None, 'параметр для форммы!'),
        'signature':(None, 'параметр для форммы!'),
        'params': (None, 'параметр для форммы!')
    }
    resp = requests.post(url, files=file)
```

## Многопоточность
```python
import concurrent.futures
import threading

loc = threading.Lock() # создать "затычку" для потока (пока эту операцию не выполнит один поток, другой не начнет)
with loc: # пример работы "затычки"
    pass
# Ниже пример создание потоков. Не выдает исключения если функция отработала не так
# max_workers=4 - количество потоков, test_func имя функции которая будет выполняться в многопотоке
# функция должа быть обязательно с аргументами. range(10) - количество выполнений
def test_func(a=1):
    pass
with concurrent.futures.ThreadPoolExecutor(max_workers=4) as executor:
    executor.map(test_func, range(10))
```

## Работа с картинками
Это сторонняя библиотека. Требует установки. 
Оф документация: [https://pillow.readthedocs.io/en/stable/](https://pillow.readthedocs.io/en/stable/)

    python -m pip install --upgrade pip
    python -m pip install --upgrade Pillow
```python
from PIL import Image
img = Image.open(path) # открыть картинку для обработки
w, h = img.size # получить ширину и высоту в переменные int
img.resize((100, 200), Image.ANTIALIAS) # изменить размер картинки 100х200
img.save(path, quality=90) # сохранить изображение, опционно можно выбрать качество
thumb_img = Image.new('RGB', (100, 100)) # создать новую картинку
thumb_img.paste(img, (0,50)) # вставить картинку в картинку по координатам
def img_resize(path):
    # функция для пропорционального изменения картинки по ширине
    img = Image.open(path)
    w, h = img.size
    new_w = 800
    new_h = int(new_w * h / w)
    img = img.resize((new_w, new_h), Image.ANTIALIAS)
    img.save(path)
```

## Парсинг
Это сторонняя библиотека. Требует установки. 
Оф документация: [https://www.crummy.com/software/BeautifulSoup/bs4/doc/](https://www.crummy.com/software/BeautifulSoup/bs4/doc/)

    pip install beautifulsoup4

Дополнительно установить парсер `lxml`

    pip install lxml

```python
from bs4 import BeautifulSoup
import lxml

html = requests.get('https://site.com')
pars = BeautifulSoup(html, 'lxml') # Создаем объект для парсинга
# Находит один элемент по заданным парраметрам. Можно указывать класс и другие
# хтмл атрибуты
h1 = pars.find('h1', _class='h1', id=False, attrs={'title':True})
p2 = pars.find_all('a', class_='text') # Тоже самое что и find, только возвращает
# список результатов
link = p2.get('href') # Получить любой атрибут выпаршенного объекта
```

## Рандом
```python
import random

list1 = ['world', 'link', 'premium']
rand = random.choice(list1) # Возвращает рандомный элемент последовательности
```