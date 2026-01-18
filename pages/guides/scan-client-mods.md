---
title: Сканирование сервера на клиентские моды
description: Как проверить папку mods на сервере и найти клиентские моды с помощью ModsChecker.
---

ModsChecker - CLI-утилита для аудита модов Minecraft. Она сканирует папку `mods`, считает хэши и пытается определить клиентские моды через Modrinth/CurseForge и метаданные модов.

## Шаг 1: Подготовьте Java и скачайте ModsChecker
Для запуска нужен Java 8+.

Скачайте готовый jar из релизов:
https://github.com/multivarka1/modschecker/releases/latest

## Шаг 2: Подготовьте папку с модами
Положите `modschecker.jar` в корень сервера рядом с папкой `mods`.
Пример структуры:
```
home/container/
  mods/
  modschecker.jar
```

## Шаг 3: Запустите сканирование
Запустите утилиту из корня сервера:
```bash
java -jar modschecker.jar
```

Если хотите получить отчет в JSON:
```bash
java -jar modschecker.jar --jsonOutput report.json
```

Для более точного определения модов можно добавить ключ CurseForge:
```bash
java -jar modschecker.jar --curseforgeApiKey <key>
```

Если нужно поменять путь к `mods`, язык или другие параметры, сделайте это в `modschecker.properties`.
Ключ CurseForge можно указать либо флагом, либо в `modschecker.properties` как `curseforgeApiKey`.

## Шаг 4: Проверьте результаты
В отчете будут пометки о клиентских модах. Их нужно убрать с сервера и оставить только на клиенте. Если мод помечен опциональным, перепроверьте его документацию перед удалением.

!> Утилита ничего не удаляет и не меняет — она только анализирует содержимое папки `mods`.
