---
# Front matter
lang: ru-RU
title: "Лабораторная работа № 2"
subtitle: "Дискреционное разграничение прав в Linux. Основные атрибуты."
author: "Алибаева Данагуль НБибд-01-18"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Задание

1. В установленной при выполнении предыдущей лабораторной работы операционной системе создайте учётную запись пользователя guest (использую учётную запись администратора)

2. Задайте пароль для пользователя guest (использую учётную запись администратора)

3. Войдите в систему от имени пользователя guest.

4. Определите директорию, в которой вы находитесь, командой pwd.

5. Уточните имя вашего пользователя командой whoami.

6. Уточните имя вашего пользователя, его группу, а также группы, куда входит пользователь.

7. Сравните полученную информацию об имени пользователя с данными, выводимыми в приглашении командной строки. 

8. Определите uid пользователя. Определите gid пользователя.

9. Определите существующие в системе директории.

10. Проверьте, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home.

11. Создайте в домашней директории поддиректорию dir1.

12. Снимите с директории dir1 все атрибуты dir1 и проверьте её. 

13. Попытайтесь создать в директории dir1 файл file1. 

14. Заполните таблицу «Установленные права и разрешённые действия», выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет. Если операция разрешена, занесите в таблицу знак «+», если не разрешена, знак «-».

15. На основании заполненной таблицы определите те или иные минимально необходимые права для выполнения операций внутри директории dir1, заполните таблицу.


# Теоретическое введение

Атрибуты файла - это набор из девяти основных битов. Определяющих какие из пользователей обладают правами на чтение, запись, а также запуск файлов для выполнения. Данный набор формирует код, называемый режимом доступа к файлу/каталогу. Первые три бита определяют права доступа для владельца. Следующие — для группы пользователей, к которой относится файл и последние три бита — права доступа для всех остальных пользователей в системе. [1]

Существует также ещё четыре дополнительных бита. Которые определяют тип самого файла и задаются непосредственно при создании файла. С помощью команды chmod можно менять основные (и некоторые дополнительные) биты режима доступа. Сделать это может только владелец файла или суперпользователь. Просматривать атрибуты (в том числе и режимы доступа) позволяет команда ls. Таким образом, характер поведения ФС, а также распределение доступа и управление им полностью определяется атрибутами файлов. Которые хранит сама ФС — это самодостаточный и универсальный подход. [1]

Для записи кода режима доступа используется восьмеричная запись чисел. Как уже было отмечено, код доступа содержит три «триады» битов — для пользователя, группы и всех остальных, именно в таком порядке. Битам из первой триады соответствуют значения в восьмеричной записи 400, 200 и 100. Для второй триады (т. е. для группы) — 40, 20 и 10. Наконец, для третьей (все остальные) — 4, 2 и 1. В свою очередь, первому биту в каждой триаде соответствует доступ на чтение (r — «read»). Второму — на запись (w — «write») и третьему — на выполнение, т. е. x — «execute». [1]

Установка бита чтения (r) в одной из триад (или во всех) задаёт право открывать данный файл для чтения соответствующим категориям пользователей. Наличие бита записи (w) позволяет изменять файл. При этом возможно его удаление и/или переименование файла, но только в том случае, если заданы соответствующие биты для его родительского каталога, поскольку именно в его записях хранятся имена файлов. [1]

# Выполнение лабораторной работы

1.Лабораторная работа выполнялась дома со следующими характеристиками техники: 

– Intel(R) Core(TM) i5-8300H CPU @ 2.30GHz, 2304 МГц, ядер: 4, логических процессоров: 8

– ОС Майкрософт Windows 10 Pro

– VirtualBox верс. 6.1.26

2. В установленной при выполнении предыдущей лабораторной работы операционной системе запустила терминал и перешла под учетную запись root с помощью команды su (рис. -@fig:001)

![Переход под учетную запись root](image/ris1_1.png){ #fig:001 width=70% }

3. Создала учётную запись пользователя guest (используя учётную запись администратора): с помощью команды useradd guest (рис. -@fig:002)

![Создание учетной записи пользователя guest](image/ris1_2.png){ #fig:002 width=70% }

4. Задала пароль для пользователя guest (используя учётную запись администратора): passwd guest (рис. -@fig:003)

![Задание пароля для пользователя guest](image/ris1_3.png){ #fig:003 width=70% }

5. Вошла в систему от имени пользователя guest (рис. -@fig:004)

![Вход в систему от имени пользователя guest](image/ris1_4.png){ #fig:004 width=70% }

6. Определила директорию, в которой я нахожусь, командой pwd. Определила, что она является моей домашней директорией (рис. -@fig:005)

![Определение директории](image/ris1_5.png){ #fig:005 width=70% }

7. Уточнила имя пользователя командой whoami (рис. -@fig:006)

![Уточнение имени пользователя](image/ris1_6.png){ #fig:006 width=70% }

8. Уточнила имя пользователя, его группу, а также группы, куда входит пользователь, командой id. Сравнила вывод id с выводом команды groups. Команда groups выводит нам только название группы (рис. -@fig:007)

![Уточнение группы имени пользователя](image/ris1_7.png){ #fig:007 width=70% }

9. Сравнила полученную информацию об имени пользователя с данными, выводимыми в приглашении командной строки. В командной строке у нас выводится еще и имя пользователя.

10. Просмотрела файл /etc/passwd командой cat /etc/passwd (рис. -@fig:008). Нашла в нём свою учётную запись (рис. -@fig:009). Определила uid пользователя, который равен 1001. Определила gid пользователя, который равен 1001. Сравнила найденные значения с полученными в предыдущих пунктах и сделала вывод, что они равны.

![Просмотр файла /etc/passwd](image/ris1_8.png){ #fig:008 width=70% }

![Поиск учетной записи](image/ris1_9.png){ #fig:009 width=70% }

11. Определила существующие в системе директории командой ls -l /home/. Это dalibaeva и guest (рис. -@fig:010).  На директориях установлены полные права у владельца. Это чтение, запись и запуск директории. У группы и остальных пользователей нет никаких прав.   

![Определение существующих директорий](image/ris1_10.png){ #fig:010 width=70% }

12. Проверила, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home, командой: lsattr /home. Мне удалось увидеть расширенные атрибуты поддиректории guest, но не dalibaeva (рис. -@fig:011).

![Расширенные атрибуты на поддиректориях](image/ris1_11.png){ #fig:011 width=70% }

13. Создала в домашней директории поддиректорию dir1 командой mkdir dir1 (рис. -@fig:012). Определила, командами ls -l и lsattr, какие права доступа и расширенные атрибуты были выставлены на директорию dir1 (рис. -@fig:013). Владельцу выставлены полные права доступа (чтение, запись, запуск директории), группе пользователей – полные права, остальным пользователям – только чтение и запуск. На директорию dir1 не выставлено никаких расширенных атрибутов.

![Создание поддиректории dir1](image/ris1_12.png){ #fig:012 width=70% }

![Определение прав доступа и расширенных атрибутов](image/ris1_13.png){ #fig:013 width=70% }

14. Сняла с директории dir1 все атрибуты командой chmod 000 dir1 и проверила с её помощью правильность выполнения команды ls -l (рис. -@fig:014).

![Снятие атрибутов](image/ris1_14.png){ #fig:014 width=70% }

15. Попыталась создать в директории dir1 файл file1 командой echo "test" > /home/guest/dir1/file1 (рис. -@fig:015). При попытке, я получила отказ в доступе, так как в прошлом пункте убрала владельцу права доступа на запись. Сообщение об ошибке никак не отразилось на создании файла. Попыталась проверить командой ls -l /home/guest/dir1, находится ли файл file1 внутри директории dir1, но мне было отказано в доступе (рис. -@fig:015).

![Попытка создания файла](image/ris1_15.png){ #fig:015 width=70% }

16. Заполнила таблицу «Установленные права и разрешённые действия» (см. табл. [-@tbl:001]), выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет. Если операция разрешена, заносила в таблицу знак «+», если не разрешена, знак «-». 

17. На основании заполненной таблицы определила те или иные минимально необходимые права для выполнения операций внутри директории dir1, заполнила табл. 2.2 (см. табл. [-@tbl:002]).

: Установленные права и разрешённые действия {#tbl:001}

| Права директории | Права файла | Создание файла | Удаление файла | Запись в файл | Чтение файла | Смена директории | Просмотр файлов в директории | Переименование файла | Смена атрибутов файла |
|------------------|-------------|----------------|----------------|---------------|--------------|------------------|------------------------------|----------------------|-----------------------|
| d--- (000)        | --- (000)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d--- (000)        | --x (100)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d--- (000)        | -w- (200)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d--- (000)        | -wx (300)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d--- (000)        | r-- (400)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d--- (000)        | r-x (500)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d--- (000)        | rw- (600)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d--- (000)        | rwx (700)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d--x (100)        | --- (000)   | -              | -              | -             | -            | +                | -                            | -                    | +                     |
| d--x (100)        | --x (100)   | -              | -              | -             | -            | +                | -                            | -                    | +                     |
| d--x (100)        | -w- (200)   | -              | -              | +             | -            | +                | -                            | -                    | +                     |
| d--x (100)        | -wx (300)   | -              | -              | +             | -            | +                | -                            | -                    | +                     |
| d--x (100)        | r-- (400)   | -              | -              | -             | +            | +                | -                            | -                    | +                     |
| d--x (100)        | r-x (500)   | -              | -              | -             | +            | +                | -                            | -                    | +                     |
| d--x (100)        | rw- (600)   | -              | -              | +             | +            | +                | -                            | -                    | +                     |
| d--x (100)        | rwx (700)   | -              | -              | +             | +            | +                | -                            | -                    | +                     |
| d-w- (200)        | --- (000)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d-w- (200)        | --x (100)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d-w- (200)        | -w- (200)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d-w- (200)        | -wx (300)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d-w- (200)        | r-- (400)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d-w- (200)        | r-x (500)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d-w- (200)        | rw- (600)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d-w- (200)        | rwx (700)   | -              | -              | -             | -            | -                | -                            | -                    | -                     |
| d-wx (300)        | --- (000)   | +              | +              | -             | -            | +                | -                            | +                    | +                     |
| d-wx (300)        | --x (100)   | +              | +              | -             | -            | +                | -                            | +                    | +                     |
| d-wx (300)        | -w- (200)   | +              | +              | +             | -            | +                | -                            | +                    | +                     |
| d-wx (300)        | -wx (300)   | +              | +              | +             | -            | +                | -                            | +                    | +                     |
| d-wx (300)        | r-- (400)   | +              | +              | -             | +            | +                | -                            | +                    | +                     |
| d-wx (300)        | r-x (500)   | +              | +              | -             | +            | +                | -                            | +                    | +                     |
| d-wx (300)        | rw- (600)   | +              | +              | +             | +            | +                | -                            | +                    | +                     |
| d-wx (300)        | rwx (700)   | +              | +              | +             | +            | +                | -                            | +                    | +                     |
| dr-- (400)        | --- (000)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| dr-- (400)        | --x (100)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| dr-- (400)        | -w- (200)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| dr-- (400)        | -wx (300)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| dr-- (400)        | r-- (400)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| dr-- (400)        | r-x (500)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| dr-- (400)        | rw- (600)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| dr-- (400)        | rwx (700)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| dr-x (500)        | --- (000)   | -              | -              | -             | -            | +                | +                            | -                    | +                     |
| dr-x (500)        | --x (100)   | -              | -              | -             | -            | +                | +                            | -                    | +                     |
| dr-x (500)        | -w- (200)   | -              | -              | +             | -            | +                | +                            | -                    | +                     |
| dr-x (500)        | -wx (300)   | -              | -              | +             | -            | +                | +                            | -                    | +                     |
| dr-x (500)        | r-- (400)   | -              | -              | -             | +            | +                | +                            | -                    | +                     |
| dr-x (500)        | r-x (500)   | -              | -              | -             | +            | +                | +                            | -                    | +                     |
| dr-x (500)        | rw- (600)   | -              | -              | +             | +            | +                | +                            | -                    | +                     |
| dr-x (500)        | rwx (700)   | -              | -              | +             | +            | +                | +                            | -                    | +                     |
| drw- (600)        | --- (000)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| drw- (600)        | --x (100)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| drw- (600)        | -w- (200)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| drw- (600)        | -wx (300)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| drw- (600)        | r-- (400)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| drw- (600)        | r-x (500)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| drw- (600)        | rw- (600)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| drw- (600)        | rwx (700)   | -              | -              | -             | -            | -                | +                            | -                    | -                     |
| drwx (700)        | --- (000)   | +              | +              | -             | -            | +                | +                            | +                    | +                     |
| drwx (700)        | --x (100)   | +              | +              | -             | -            | +                | +                            | +                    | +                     |
| drwx (700)        | -w- (200)   | +              | +              | +             | -            | +                | +                            | +                    | +                     |
| drwx (700)        | -wx (300)   | +              | +              | +             | -            | +                | +                            | +                    | +                     |
| drwx (700)        | r-- (400)   | +              | +              | -             | +            | +                | +                            | +                    | +                     |
| drwx (700)        | r-x (500)   | +              | +              | -             | +            | +                | +                            | +                    | +                     |
| drwx (700)        | rw- (600)   | +              | +              | +             | +            | +                | +                            | +                    | +                     |
| drwx (700)        | rwx (700)   | +              | +              | +             | +            | +                | +                            | +                    | + 



: Минимальные права для совершения операций {#tbl:002}

| Операция               | Минимальные права на директорию | Минимальные права на файл |
|------------------------|---------------------------------|---------------------------|
| Создание файла         | 	(300)                      | 		(000)          |
| Удаление файла         | 	(300)                      |	        (000)          |
| Чтение файла           | 	(100)                      | 		(400)          |
| Запись в файл          | 	(100)                      |	        (200)          |
| Переименование файла   | 	(300)                      | 		(000)          |
| Создание поддиректории | 	(300)                      | 		(000)          |
| Удаление поддиректории | 	(300)                      | 		(000)          |




# Выводы

Получила практические навыки работы в консоли с атрибутами файлов, закрепила теоретические основы дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.

# Список литературы 

1. Атрибуты файлов в Linux // URL: https://itproffi.ru/atributy-fajlov-v-linux/ (дата обращения: 01.10.2021).