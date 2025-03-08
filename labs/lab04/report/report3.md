---
## Front matter
title: "Отчёт по лабораторной работе № 4"
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

Получение навыков правильной работы с репозиториями git.

# Задание

1. Установка git-flow
2. Установка Node.js
3. Настройка Node.js
4. Общепринятые коммиты
5. Создание репозитория git
6. Работа с репозиторием git

# Теоретическое введение

Gitflow Workflow опубликована и популяризована Винсентом Дриссеном.
Gitflow Workflow предполагает выстраивание строгой модели ветвления с учётом выпуска проекта.
Данная модель отлично подходит для организации рабочего процесса на основе релизов.
Работа по модели Gitflow включает создание отдельной ветки для исправлений ошибок в рабочей среде.
Последовательность действий при работе по модели Gitflow:
Из ветки master создаётся ветка develop.
Из ветки develop создаётся ветка release.
Из ветки develop создаются ветки feature.
Когда работа над веткой feature завершена, она сливается с веткой develop.
Когда работа над веткой релиза release завершена, она сливается в ветки develop и master.
Если в master обнаружена проблема, из master создаётся ветка hotfix.
Когда работа над веткой исправления hotfix завершена, она сливается в ветки develop и master.

Процесс работы с Gitflow
Основные ветки (master) и ветки разработки (develop)

Для фиксации истории проекта в рамках этого процесса вместо одной ветки master используются две ветки. В ветке master хранится официальная история релиза, а ветка develop предназначена для объединения всех функций. Кроме того, для удобства рекомендуется присваивать всем коммитам в ветке master номер версии.
При использовании библиотеки расширений git-flow нужно инициализировать структуру в существующем репозитории:

git flow init
Для github параметр Version tag prefix следует установить в v.
После этого проверьте, на какой ветке Вы находитесь:

git branch
Функциональные ветки (feature)

Под каждую новую функцию должна быть отведена собственная ветка, которую можно отправлять в центральный репозиторий для создания резервной копии или совместной работы команды. Ветки feature создаются не на основе master, а на основе develop. Когда работа над функцией завершается, соответствующая ветка сливается обратно с веткой develop. Функции не следует отправлять напрямую в ветку master.
Как правило, ветки feature создаются на основе последней ветки develop.
Создание функциональной ветки

Создадим новую функциональную ветку:

git flow feature start feature_branch
Далее работаем как обычно.

Окончание работы с функциональной веткой

По завершении работы над функцией следует объединить ветку feature_branch с develop:

git flow feature finish feature_branch
Ветки выпуска (release)

Когда в ветке develop оказывается достаточно функций для выпуска, из ветки develop создаётся ветка release. Создание этой ветки запускает следующий цикл выпуска, и с этого момента новые функции добавить больше нельзя — допускается лишь отладка, создание документации и решение других задач. Когда подготовка релиза завершается, ветка release сливается с master и ей присваивается номер версии. После нужно выполнить слияние с веткой develop, в которой с момента создания ветки релиза могли возникнуть изменения.
Благодаря тому, что для подготовки выпусков используется специальная ветка, одна команда может дорабатывать текущий выпуск, в то время как другая команда продолжает работу над функциями для следующего.
Создать новую ветку release можно с помощью следующей команды:

git flow release start 1.0.0
Для завершения работы на ветке release используются следующие команды:

git flow release finish 1.0.0
Ветки исправления (hotfix)

Ветки поддержки или ветки hotfix используются для быстрого внесения исправлений в рабочие релизы. Они создаются от ветки master. Это единственная ветка, которая должна быть создана непосредственно от master. Как только исправление завершено, ветку следует объединить с master и develop. Ветка master должна быть помечена обновлённым номером версии.
Наличие специальной ветки для исправления ошибок позволяет команде решать проблемы, не прерывая остальную часть рабочего процесса и не ожидая следующего цикла релиза.
Ветку hotfix можно создать с помощью следующих команд:

git flow hotfix start hotfix_branch
По завершении работы ветка hotfix объединяется с master и develop:

git flow hotfix finish hotfix_branch

# Выполнение лабораторной работы

Устанавливаем git-flow из коллекции репозиториев Copr (рис. [-@fig:001]).

![Процесс подготовки к установке](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/1.png){#fig:001 width=70%}

Установка git-flow (рис. [-@fig:002]).

![Процесс установки](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/2.png){#fig:002 width=70%}

Устанавливаем Nodejs и pnpm, далее настраиваем Nodejs (рис. [-@fig:003]).

![Процесс установки и настройки](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/4.png){#fig:003 width=70%}

Воспользуемся программой для помощи в форматировании коммитов (рис. [-@fig:004]).

![Программа](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/5.png){#fig:004 width=70%}

Воспользуемся программой для помощи в создании логов (рис. [-@fig:005]).

![Программа](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/6.png){#fig:005 width=70%}

Создаем репозиторий, делаем первый коммит и выкладываем на гитхаб (рис. [-@fig:006]).

![Отправка коммита](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/8.png){#fig:006 width=70%}

Сконфигурим формат коммитов. Для этого добавим в файл package.json команду для формирования коммитов (рис. [-@fig:007]).

![Исправленный файл package.json](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/9.png){#fig:007 width=70%}

Добавим новые файлы, выполним коммит, отправим на github (рис. [-@fig:008]).

![Выполнение коммита](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/10.png){#fig:008 width=70%}

Инициализируем git-flow (рис. [-@fig:009]).

![Выполнение коммита](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/11.png){#fig:009 width=70%}

Загружаем весь репозиторий в хранилище, установим внешнюю ветку как вышестоящую для этой ветки, создадим релиз с версией 1.0.0 (рис. [-@fig:010]).

![Загрузка репозитория, создание релиза](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/12.png){#fig:010 width=70%}

Создаем журнал изменений, добавляем журнал изменений в индекс, заливаем релизную ветку в основную ветку (рис. [-@fig:011]).

![Создание журнала, добавление журнала, залитие релизной ветки](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/14.png){#fig:011 width=70%}

Создаем ветку для новой функциональности, по окончании разработки новой функциональности объединяем ветку feature_branch c develop (рис. [-@fig:012]).

![Создаем и объединяем ветки](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/15.png){#fig:012 width=70%}

Обновите номер версии в файле package.json. Установите её в 1.2.3 (рис. [-@fig:013]).

![Обновленный номер версии в файле](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/16.png){#fig:013 width=70%}

Создадем релиз с версией 1.2.3, создадим журнал изменений (рис. [-@fig:014]).

![Создание релиза, создание журнала](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/17.png){#fig:014 width=70%}

Добавляем журнал изменений в индекс, заливаем релизную ветку в основную ветку (рис. [-@fig:015]).

![Создание релиза, создание журнала](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/18.png){#fig:015 width=70%}

Отправляем данные на Github (рис. [-@fig:016]).

![Отправка данных на Github](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab04/report/image/20.png){#fig:016 width=70%}

# Выводы

После выполнения данной лабораторной работы я получил навыки правильной работы с репозиториями git.

# Список литературы{.unnumbered}

Курс Архитектура компьютеров и операционные системы. Раздел "Операционные системы" Лабораторная работа № 4 ТУИС РУДН.
