---
## Front matter
title: "Отчёт по лабораторной работе № 1"
author: "Веретенников Дмитрий Олегович НКАбд-01-24"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Задание

1. Установка операционной системы.
2. Настройка операционной системы и загрузка необходимых программ.

# Выполнение лабораторной работы

Устанавливаем средства разработки (рис. [-@fig:001]).

![Процесс установки средства разработки](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab01/report/image/1.png){#fig:001 width=70%}

Обновляем все пакеты (рис. [-@fig:002]).

![Процесс обновления всех пакетов](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab01/report/image/2.png){#fig:002 width=70%}

Устанавливаем программы для повышения комфорта работы (рис. [-@fig:003]).

![Процесс установки](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab01/report/image/3.png){#fig:003 width=70%}

Настраиваем раскладку клавиатуры (рис. [-@fig:004]).

![Редактируем конфигурационный файл /etc/X11/xorg.conf.d/00-keyboard.conf](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab01/report/image/4.png){#fig:004 width=70%}

Устанавливаем дистрибутив TeXlive (рис. [-@fig:005]).

![Процесс установки](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab01/report/image/5.png){#fig:005 width=70%}

Выполняем команду dmesg | less (рис. [-@fig:006]).

![Итог выполнение команды](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab01/report/image/6.png){#fig:006 width=70%}

С помощью команды dmesg | grep выполняю домашнее задание (рис. [-@fig:007]).

![Итог выполнения команды](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab01/report/image/7.png){#fig:007 width=70%}

![Итог выполнения команды](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab01/report/image/8.png){width=70%}

# Ответы на контрольные вопросы

Учётная запись пользователя
Учётная запись пользователя в операционной системе включает следующую информацию:

Имя пользователя (логин).
Идентификатор пользователя (UID).
Домашний каталог (обычно /home/username).
Группу пользователя (GID), а также дополнительные группы, к которым принадлежит пользователь.
Пароль (хранится в зашифрованной форме).
Комментарий (иногда используется для описания пользователя).
Информация о сроках истечения пароля и блокировке аккаунта.
Основные команды терминала
Получение справки по команде:

man <команда> Открывает руководство


cd <каталог> Переход в указанный каталог


ls Просмотреть содержимое текущего каталога

mkdir <имя_каталога> Создать новый каталог

rm <имя_файла> Удалить файл

history Вывести историю выполненных команд

Файловая система — это способ организации хранения и управления файлами на носителе данных (жёсткий диск, SSD и др.). Она определяет структуру каталогов, способы именования файлов, методы доступа к данным и другие параметры.

Примеры файловых систем:

ext4 (Linux): Расширенная файловая система четвёртого поколения, широко используемая в Linux-системах. Поддерживает журналирование, большие объёмы данных и хорошую производительность.
NTFS (Windows): Стандартная файловая система для Windows NT. Обеспечивает высокую надёжность благодаря поддержке журналирования и безопасности.
FAT32: Универсальная файловая система, совместимая с различными операционными системами. Ограничена размером файла до 4 ГБ и разделов до 8 ТБ.
APFS (macOS): Новая файловая система от Apple, оптимизированная для флеш-накопителей и SSD. Обладает улучшенной производительностью и поддержкой шифрования.
Просмотр смонтированных файловых систем
Для просмотра всех смонтированных файловых систем в Unix-подобных системах используйте команду mount:


mount
Она выведет список всех активных точек монтирования с указанием типа файловой системы.

Также можно использовать команду df, чтобы увидеть используемые файловые системы и занимаемое место:


df -h
Чтобы завершить зависший процесс, сначала нужно узнать его идентификатор (PID). Для этого выполните команду:


ps aux | grep <название_процесса>
или


top 
Затем завершите процесс командой kill:


kill <PID>
Если процесс не реагирует на обычное завершение, попробуйте принудительное завершение:


kill -9 <PID>


# Выводы

После выполнения данной лабораторной работы приобрел практические навыки установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.

# Список литературы{.unnumbered}

Курс Архитектура компьютеров и операционные системы. Раздел "Операционные системы" Лабораторная работа № 1 ТУИС РУДН.
