---
## Front matter
lang: ru-RU
title: Лабораторная работа №3
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

Получение практических навыков работы в консоли с атрибутами файлов для групп пользователей. 



## Задачи выполнения лабораторной работы

1. В установленной операционной системе создать учётную запись пользователя guest (используя учётную запись администратора)

2. Задать пароль для пользователя guest (используя учётную запись администратора)

3. Аналогично создать второго пользователя guest2

4. Добавить пользователя guest2 в группу guest

5. Осуществить вход в систему от двух пользователей на двух разных консолях





## Задачи выполнения лабораторной работы

6. Для обоих пользователей определить директорию, в которой находимся. Сравните её с приглашениями командной строки.

7. Уточнить имя пользователя, его группу, кто входит в неё и к каким группам принадлежит он сам. Определить в какие группы входят пользователи guest и guest2. Сравнить вывод команды groups с выводом команд id -Gn и id -G.

8. Сравнить полученную информацию с содержимым файла /etc/group

9. От имени пользователя guest2 выполнить регистрацию пользователя guest2 в группе guest


## Задачи выполнения лабораторной работы

10. От имени пользователя guest изменить права директории /home/guest, разрешив все действия для пользователей группы

11. От имени пользователя guest снять с директории /home/guest/dir1 все атрибуты и проверить правильность снятия атрибутов. Меняя атрибуты у директории dir1 и файла file1 от имени пользователя guest и делая проверку от пользователя guest2, заполнить табл. 3.1, определив опытным путём, какие операции разрешены, а какие нет. Если операция разрешена, занесите в таблицу знак «+», если не разрешена, знак «-».

Сравнить табл. 2.1 (из лабораторной работы № 2) и табл. 3.1. На основании заполненной таблицы определите те или иные минимально необходимые права для выполнения пользователем guest2 операций внутри директории dir1 и заполните табл. 3.2.


## Результаты выполнения лабораторной работы

1. Созданная учётная запись пользователя guest2 (рис. -@fig:001). 
 
![Создание учетной записи пользователя guest2](image/1_3.png){ #fig:001 width=70% }  

## Результаты выполнения лабораторной работы

2. Составленная таблица установленных прав и разрешённых действий для групп. (рис. -@fig:002). 

![Установленные права и разрешённые действия для групп](image/tabl3_1.png){ #fig:002 width=70% }  

## Результаты выполнения лабораторной работы

3. Составленная таблица минимальных прав для совершения операций от имени пользователя входящих в группу (рис. -@fig:003). 

![Минимальные права для совершения операций от имени пользователя входящих в группу](image/tabl3_2.png){ #fig:003 width=50% }  


## Вывод

Получила практические навыки работы в консоли с атрибутами файлов для групп пользователей.





## {.standout}

Спасибо за внимание 
