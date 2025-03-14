---
## Front matter
lang: ru-RU
title: Лабораторная работа №2
author:
  - Веретенников Д. О.
institute:
  - Российский университет дружбы народов, Москва, Россия

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Веретенников Дмитрий Олегович
  * НКАбд-01-24 ст.билет №1132240687
  * Студент 1 Курса
  * Российский университет дружбы народов
  * <https://github.com/doveretennikov/study_2024-2025_os-intro>

:::
::: {.column width="30%"}

:::
::::::::::::::

# Вводная часть

## Цели и задачи

- Изучить идеологию и применение средств контроля версий.
- Освоить умения по работе с git.
- Установка программного обеспечения. 
- Базовая настройка git.
- Настройка рабочего пространства курса.

## Теоретическое введение

Системы контроля версий (Version Control System, VCS) применяются при работе нескольких человек над одним проектом. Обычно основное дерево проекта хранится в локальном или удалённом репозитории, к которому настроен доступ для участников проекта. При внесении изменений в содержание проекта система контроля версий позволяет их фиксировать, совмещать изменения, произведённые разными участниками проекта, производить откат к любой более ранней версии проекта, если это требуется.

В классических системах контроля версий используется централизованная модель, предполагающая наличие единого репозитория для хранения файлов. Выполнение большинства функций по управлению версиями осуществляется специальным сервером. Участник проекта (пользователь) перед началом работы посредством определённых команд получает нужную ему версию файлов. После внесения изменений, пользователь размещает новую версию в хранилище. При этом предыдущие версии не удаляются из центрального хранилища и к ним можно вернуться в любой момент.

## Теоретическое введение

 Сервер может сохранять не полную версию изменённых файлов, а производить так называемую дельта-компрессию — сохранять только изменения между последовательными версиями, что позволяет уменьшить объём хранимых данных.

Системы контроля версий поддерживают возможность отслеживания и разрешения конфликтов, которые могут возникнуть при работе нескольких человек над одним файлом. Можно объединить (слить) изменения, сделанные разными участниками (автоматически или вручную), вручную выбрать нужную версию, отменить изменения вовсе или заблокировать файлы для изменения. В зависимости от настроек блокировка не позволяет другим пользователям получить рабочую копию или препятствует изменению рабочей копии файла средствами файловой системы ОС, обеспечивая таким образом, привилегированный доступ только одному пользователю, работающему с файлом.

## Теоретическое введение

Системы контроля версий также могут обеспечивать дополнительные, более гибкие функциональные возможности. Например, они могут поддерживать работу с несколькими версиями одного файла, сохраняя общую историю изменений до точки ветвления версий и собственные истории изменений каждой ветви. Кроме того, обычно доступна информация о том, кто из участников, когда и какие изменения вносил. Обычно такого рода информация хранится в журнале изменений, доступ к которому можно ограничить.
В отличие от классических, в распределённых системах контроля версий центральный репозиторий не является обязательным.
Среди классических VCS наиболее известны CVS, Subversion, а среди распределённых — Git, Bazaar, Mercurial. Принципы их работы схожи, отличаются они в основном синтаксисом используемых в работе команд.

# Выполнение Лабораторной работы №2

## Установка программного обеспечения

Устанавливаем git и gh.

![Процесс установки git и gh](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/1.png){#fig:001 width=55%}

## Базовая настройка git

Задаём имя и email владельца репозитория. Далее настраиваем utf-8 в выводе сообщений git. После этого задаём имя начальной ветки, параметр autocrlf и параметр safecrlf.

![Процесс базовой настройки git](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/2.png){#fig:002 width=55%}

## Создание ключей SSH

Создаём ключи ssh. С начала ключ по алгоритму rsa, а потом по алгоритму ed25519.

![Процесс создание ключей ssh](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/3.png){#fig:003 width=55%}

## Создание ключей SSH

Создаём ключи ssh. С начала ключ по алгоритму rsa, а потом по алгоритму ed25519.

![Процесс создание ключей ssh](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/4.png){#fig:004 width=55%}

## Создание ключа PGP

Создаём ключ pgp.

![Процесс создание ключа pgp](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/5.png){#fig:005 width=55%}

## Добавление PGP ключа в GitHub

Выводим список ключей и копируем отпечаток приватного ключа.

![Список ключей](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/6.png){#fig:006 width=55%}

## Копирование PGP ключа

Копирую сгенерированный PGP ключ в буфер обмена.

![Копирование ключа PGP](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/7.png){#fig:007 width=55%}

## Настройка автоматических подписей коммитов git

Используя введеный email, указываем git применять его при подписи коммитов.

![Настройки автоматических подписей коммитов git](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/8.png){#fig:008 width=55%}

## Настройка gh

Авторизовываюсь через gh.

![Настройка gh](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/9.png){#fig:009 width=55%}

## Создание репозитория курса на основе шаблона

Создаю репозиторий курса на основе шаблона.

![Процесс создания репозитория курса на основе шаблона](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/10.png){#fig:010 width=55%}

## Копирование шаблона репозитория

Клонирую шаблон репозитория.

![Клонирования шаблона репозитория](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/12.png){#fig:011 width=55%}

## Настройка каталога курса

Настраиваю каталог курса, удаляю лишние файлы и создаю необходимые каталоги, затем отправляю всё на сервер.

![Настройка каталога курса](/home/doveretennikov/work/study/2024-2025/Операционные системы/os-intro/labs/lab02/presentation/presentation/image/14.png){#fig:012 width=55%}

# Ответы на контрольные вопросы

## Вопросы

1. Системы контроля версий (Version Control System, VCS) применяются при работе нескольких человек над одним проектом. Обычно основное дерево проекта хранится в локальном или удалённом репозитории, к которому настроен доступ для участников проекта. При внесении изменений в содержание проекта система контроля версий позволяет их фиксировать, совмещать изменения, произведённые разными участниками проекта, производить откат к любой более ранней версии проекта, если это требуется. Системы контроля версий поддерживают возможность отслеживания и разрешения конфликтов, которые могут возникнуть при работе нескольких человек над одним файлом. Можно объединить (слить) изменения, сделанные разными участниками (автоматически или вручную), вручную выбрать нужную версию, отменить изменения вовсе или заблокировать файлы для изменения. В зависимости от настроек блокировка не позволяет другим пользователям получить рабочую копию или препятствует изменению рабочей копии файла средствами файловой системы ОС, обеспечивая таким образом, привилегированный доступ только одному пользователю, работающему с файлом.

## Вопросы

2. В классических системах контроля версий используется централизованная модель, предполагающая наличие единого репозитория для хранения файлов. Выполнение большинства функций по управлению версиями осуществляется специальным сервером. Участник проекта (пользователь) перед началом работы посредством определённых команд получает нужную ему версию файлов. После внесения изменений, пользователь размещает новую версию в хранилище. При этом предыдущие версии не удаляются из центрального хранилища и к ним можно вернуться в любой момент. Сервер может сохранять не полную версию изменённых файлов, а производить так называемую дельта-компрессию — сохранять только изменения между последовательными версиями, что позволяет уменьшить объём хранимых данных.

## Вопросы

3. В классических системах контроля версий используется централизованная модель, предполагающая наличие единого репозитория для хранения файлов.  В отличие от классических, в распределённых системах контроля версий центральный репозиторий не является обязательным. Среди классических VCS наиболее известны CVS, Subversion, а среди распределённых — Git, Bazaar, Mercurial.
4. 1. получение фалов с сервера 2. изменения файлов 3. отправка файлов на сервер.
5. 1. получение нужной версии файлов 2. изменения файлов 3. отправка файлов на сервер, объединение изменений если возникают конфликты при работе над файлом несколькими людьми.

# Результаты

## Выводы

После выполнения данной лабораторной работы я освоил навыка настройки и работы git, изучил идеологию и применения контроля версий.

# Список литературы

Курс Архитектура компьютеров и операционные системы. Раздел "Операционные системы" Лабораторная работа № 2 ТУИС РУДН.
