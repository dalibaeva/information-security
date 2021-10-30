---
## Front matter
lang: ru-RU
title: Лабораторная работа №4
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

Практические навыки работы в консоли с расширенными атрибутами файлов и правами доступа понадобятся для умения разграничения и избирательного управления доступом.

## Цель выполнения лабораторной работы

Получение практических навыков работы в консоли с расширенными атрибутами файлов.

## Задачи выполнения лабораторной работы

1. От имени пользователя guest определить расширенные атрибуты файла /home/guest/dir1/file1

2. Установить на файл file1 права, разрешающие чтение и запись для владельца файла.

3. Попробовать установить на файл /home/guest/dir1/file1 расширенный атрибут a от имени пользователя guest. В ответ должны получить отказ от выполнения операции.

4. Зайти на третью консоль с правами администратора либо повысить свои права. Попробовать установить расширенный атрибут a на файл /home/guest/dir1/file1 от имени суперпользователя.

5. От пользователя guest проверить правильность установления атрибута.

## Задачи выполнения лабораторной работы

6. Выполнить дозапись в файл file1 слова «test». После этого выполнить чтение файла file1. Убедиться, что слово test было успешно записано в file1.

7. Попробовать удалить файл file1 либо стереть имеющуюся в нём информацию. Попробовать переименовать файл.

8. Попробовать установить на файл file1 права, например, запрещающие чтение и запись для владельца файла. Проверить удалось ли успешно выполнить указанные команды.

9. Снять расширенный атрибут a с файла /home/guest/dirl/file1 от имени суперпользователя. Повторить операции, которые ранее не удавалось выполнить. Наблюдения занести в отчёт.

10. Повторить действия по шагам, заменив атрибут «a» атрибутом «i». Проверить удалось ли дозаписать информацию в файл. Наблюдения занести в отчёт.

## Результаты выполнения лабораторной работы

1. Успешное установление расширенного атрибута a на файл /home/guest/dir1/file1 от имени суперпользователя.
 
![Успешное выполнение команды chattr +a file1](image/1_5.png){ #fig:001 width=70% }  

## Результаты выполнения лабораторной работы

2. Успешное установление расширенного атрибута i на файл /home/guest/dir1/file1 от имени суперпользователя и осуществление некоторых действий.

![Действия с расширенным атрибутом i на файле](image/1_11.png){ #fig:002 width=70% }  

## Вывод

В результате выполнения работы я повысила свои навыки использования интерфейса командой строки (CLI), познакомилась на примерах с тем, как используются основные и расширенные атрибуты при разграничении доступа. Имела возможность связать теорию дискреционного разделения доступа (дискреционная политика безопасности) с её реализацией на практике в ОС Linux. Опробовала действие на практике расширенных атрибутов «а» и «i».

## {.standout}

Спасибо за внимание!