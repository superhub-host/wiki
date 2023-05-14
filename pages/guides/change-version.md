---
title: Смена версии сервера
description: Инструкция по изменению версии Minecraft на сервере.
---

После оплаты заказа ваш сервер автоматически устанавливается со стандартными параметрами.

При покупке Minecraft сервера, по умолчанию устанавливается последний билд. Исключением являются случаи, когда клиент покупает сервер, имеющий менее 2 Гб ОЗУ, тогда по умолчанию устанавливается версия 1.12.2, потребляющая меньше оперативной памяти. Тем не менее, клиент всегда может установить любую другую версию. Для этого нужно:

1. Перейти в панель управления и произвести вход, используя данные своего аккаунта
2. Скачать ядро нужной версии (ссылки можно найти ниже). Учтите, что установить зачастую можно только то ядро, которое было указано при покупке сервера. Если необходимо изменить Paper (Java Edition) на, к примеру, PMMP (Bedrock Edition), необходимо обратиться в тех. поддержку.
3. Переименовать скачанный файл в `server.jar`, **либо** изменить название запускаемого файла в разделе "Запуск", если имеется такая возможность.
4. Переместить скачанный файл в корневую папку сервера с помощью встроенного файлового менеджера в панели (вкладка "Управление файлами") или [стороннего клиента](/guides/use-sftp).
5. Если карта уже была сгенерирована на другой версии сервера, её необходимо удалить, дабы избежать конфликтов.
6. Перезагрузить сервер.

## Ссылки на скачивание
На всех серверах хостинга используется ОС Linux (Ubuntu), поэтому, если имеется выбор ОС, нужно выбрать именно версию для Linux.

| Проект            | Где скачать? |
| :---              | :---         |
| Vanilla (Java)    | В официальном лаунчере: "Установки" -> "Новая установка", выбрать нужную версию и нажать на "Сервер" над полем с выбором версии. |
| Spigot            | Официальных готовых сборок нет. Инструкции по сборке из исходников через BuildTools: https://www.spigotmc.org/wiki/buildtools/ |
| Paper             | На официальном сайте: https://papermc.io/downloads/paper (последняя версия Minecraft), https://papermc.io/downloads/all (все версии Minecraft) |
| Forge             | На официальном сайте: https://files.minecraftforge.net/net/minecraftforge/forge/ (выбрать "Installer", скачать и запустить на компьютере, потом загрузить сгенерированные установщиком файлы на хостинг) |
| Fabric            | На официальном сайте: https://fabricmc.net/use/ (установщик: скачать и запустить на компьютере, потом загрузить сгенерированные им файлы на хостинг) |
| BungeeCord        | Jenkins: https://ci.md-5.net/job/BungeeCord/ |
| Velocity          | На официальном сайте: https://papermc.io/downloads/velocity |
| Vanilla (Bedrock) | На официальном сайте: https://www.minecraft.net/en-us/download/server/bedrock |
| PocketMine MP     | GitHub: https://github.com/pmmp/PocketMine-MP/releases |
| Nukkit            | Jenkins: https://ci.opencollab.dev/job/NukkitX/job/Nukkit/job/master/ |
| PowerNukkit       | GitHub: https://github.com/PowerNukkit/PowerNukkit/releases |
| PowerNukkitX      | GitHub: https://github.com/PowerNukkitX/PowerNukkitX/releases |
| Geyser            | Jenkins: https://ci.opencollab.dev/job/GeyserMC/job/Geyser/job/master/ |

## Возможные проблемы

### Изменение новой версии на старую
Бывают случаи, когда клиенты сначала пытаются запустить их сервер с устанавливаемой по умолчанию версией, а потом устанавливают более старую. В таком случае, да и в целом, когда устанавливается более старая версия, возникает следующая ошибка:
```log
[17:38:24 WARN]: java.lang.RuntimeException: Server attempted to load chunk saved with newer version of minecraft! 2586 > 1343
[17:38:24 WARN]:        at net.minecraft.server.v1_12_R1.ChunkRegionLoader.a(ChunkRegionLoader.java:104)
[17:38:24 WARN]:        at net.minecraft.server.v1_12_R1.ChunkRegionLoader.loadChunk(ChunkRegionLoader.java:83)
[17:38:24 WARN]:        at org.bukkit.craftbukkit.v1_12_R1.chunkio.ChunkIOProvider.callStage1(ChunkIOProvider.java:23)
[17:38:24 WARN]:        at org.bukkit.craftbukkit.v1_12_R1.chunkio.ChunkIOProvider.callStage1(ChunkIOProvider.java:16)
[17:38:24 WARN]:        at org.bukkit.craftbukkit.v1_12_R1.util.AsynchronousExecutor.skipQueue(AsynchronousExecutor.java:336)
```

Связана эта ошибка с тем, что сервер не может загрузить мир, сохранённый с более новой версией игры. Самое простое решение в таком случае - удалить мир, чтобы сервер сгенерировал его заново.

### Загрузка Forge вместо Paper
Если Вам нужен Forge сервер, то самый идеальный вариант - купить этот сервер сразу. В случае установки Forge вместо Paper, велика вероятность, что Вы столкнётесь с подобной ошибкой:
```log
A problem occurred running the Server launcher.java.lang.reflect.InvocationTargetException
        at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.base/java.lang.reflect.Method.invoke(Method.java:566)
        at net.minecraftforge.fml.relauncher.ServerLaunchWrapper.run(ServerLaunchWrapper.java:70)
        at net.minecraftforge.fml.relauncher.ServerLaunchWrapper.main(ServerLaunchWrapper.java:34)
Caused by: java.lang.ClassCastException: class jdk.internal.loader.ClassLoaders$AppClassLoader cannot be cast to class java.net.URLClassLoader (jdk.internal.loader.ClassLoaders$AppClassLoader and java.net.URLClassLoader are in module java.base of loader 'bootstrap')
        at net.minecraft.launchwrapper.Launch.<init>(Launch.java:34)
        at net.minecraft.launchwrapper.Launch.main(Launch.java:28)
        ... 6 more
```

Дело в том, что Forge не поддерживает Java 9 и выше, в то время как для большей части серверов стандартной является Java 11. Чтобы решить проблему, достаточно изменить версию Java. Для этого перейдите во вкладку "Запуск" панели и выберите Docker образ `quay.io/pterodactyl/core:java`. Если у Вас нет возможности изменить образ, обратитесь в техническую поддержку. Подробнее об изменении версии Java можно узнать [здесь](/guides/change-java).
