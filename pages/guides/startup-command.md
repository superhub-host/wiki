---
title: Изменить команду запуска
description: Инструкция по изменении команды запуска на вашем сервере.
---

В данном гайде представлен обзор стандартных аргументов JVM (Java Virtual Machine) для сервера Minecraft для различных ядер.

## Minecraft Java Edition
### Ядро Vanilla
Официальный сервер для Java Edition, не поддерживающий плагины/моды.

Стандартные аргументы JVM: `-Xms128M -XX:MaxRAMPercentage=95.0`

### Ядро Paper
Оптимизированный сервер с поддержкой плагинов для Bukkit и Spigot.

Стандартные аргументы JVM: `-Xms128M -XX:MaxRAMPercentage=95.0 -Dterminal.jline=false -Dterminal.ansi=true`

### Ядро Purpur
Форк Paper, добавляющий новые игровые механики, поддерживающий плагины для Bukkit/Spigot/Paper.

Стандартные аргументы JVM: `-Xms128M -XX:MaxRAMPercentage=95.0 -Dterminal.jline=false -Dterminal.ansi=true`

### Ядро Forge
Сервер с поддержкой Forge модов.

Стандартные аргументы JVM: `-Xms128M -XX:MaxRAMPercentage=95.0`

### Ядро Fabric
Сервер с поддержкой Fabric модов.

Стандартные аргументы JVM: `-Xms128M -XX:MaxRAMPercentage=95.0`

## Minecraft Proxy
### Ядро Velocity
Современный прокси-сервер для Minecraft Java Edition, не поддерживающий плагины для BungeeCord.

Стандартные аргументы JVM: `-Xms128M -XX:MaxRAMPercentage=95.0 -XX:+UseG1GC -XX:G1HeapRegionSize=4M -XX:+UnlockExperimentalVMOptions -XX:+ParallelRefProcEnabled -XX:+AlwaysPreTouch -XX:MaxInlineLevel=15`

### Ядро Waterfall
Форк BungeeCord с улучшенной стабильностью и производительностью.

Стандартные аргументы JVM: `-Xms128M -XX:MaxRAMPercentage=95.0 -Dterminal.jline=false -Dterminal.ansi=true`

### Ядро BungeeCord
Классический прокси-сервер для Minecraft Java Edition.

Стандартные аргументы JVM: `-Xms128M -XX:MaxRAMPercentage=95.0`
