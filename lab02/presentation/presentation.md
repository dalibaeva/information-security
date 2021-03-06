---
## Front matter
lang: ru-RU
title: Лабораторная работа №2
author: |
	Алибаева Данагуль  \inst{1}
	
institute: |
	\inst{1}RUDN University, Moscow, Russian Federation
	
date: 2021 Moscow, Russia

## Formatting
toc: false
slide_level: 2
theme: metropolis
header-includes: 
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true
---



## Прагматика выполнения лабораторной работы

Практические навыки работы в консоли с атрибутами файлов и правами доступа понадобятся для умения разграничения и избирательного управления доступом.



## Цель выполнения лабораторной работы

Получение практических навыков работы в консоли с атрибутами файлов, закрепление теоретических основ дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.



## Задачи выполнения лабораторной работы

1. В установленной при выполнении предыдущей лабораторной работы операционной системе создайте учётную запись пользователя guest (использую учётную запись администратора)

2. Задайте пароль для пользователя guest (использую учётную запись администратора)

3. Войдите в систему от имени пользователя guest.

4. Определите директорию, в которой вы находитесь, командой pwd.

5. Уточните имя вашего пользователя командой whoami.

6. Уточните имя вашего пользователя, его группу, а также группы, куда входит пользователь.

## Задачи выполнения лабораторной работы

7. Сравните полученную информацию об имени пользователя с данными, выводимыми в приглашении командной строки. 

8. Определите uid пользователя. Определите gid пользователя.

9. Определите существующие в системе директории.

10. Проверьте, какие расширенные атрибуты установлены на поддиректориях, находящихся в директории /home.

11. Создайте в домашней директории поддиректорию dir1.

12. Снимите с директории dir1 все атрибуты dir1 и проверьте её. 


## Задачи выполнения лабораторной работы

13. Попытайтесь создать в директории dir1 файл file1.
 
14. Заполните таблицу «Установленные права и разрешённые действия», выполняя действия от имени владельца директории (файлов), определив опытным путём, какие операции разрешены, а какие нет. Если операция разрешена, занесите в таблицу знак «+», если не разрешена, знак «-».

15. На основании заполненной таблицы определите те или иные минимально необходимые права для выполнения операций внутри директории dir1, заполните таблицу.



## Результаты выполнения лабораторной работы

1. Созданная учётная запись пользователя guest.(рис. -@fig:001). 
 
![Вход в систему от имени пользователя guest](image/ris1_4.png){ #fig:001 width=70% }  

## Результаты выполнения лабораторной работы

2. Составленная таблица установленных прав и разрешённых действий. (рис. -@fig:002). 

![Установленные права и разрешённые действия](image/tabl2_1.png){ #fig:002 width=70% }  

## Результаты выполнения лабораторной работы

3. Составленная таблица минимальных прав для совершения операций(рис. -@fig:003). 

![Минимальные права для совершения операций](image/tabl2_2.png){ #fig:003 width=50% }  


## Вывод

Получила практические навыки работы в консоли с атрибутами файлов, закрепила теоретические основы дискреционного разграничения доступа в современных системах с открытым кодом на базе ОС Linux.






## {.standout}

Спасибо за внимание 
