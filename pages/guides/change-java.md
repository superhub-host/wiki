---
title: Смена версии Java (JDK)
description: Инструкция по изменению версии Java на сервере в панели.
redirect: /guides/minecraft/java-version
---

По умолчанию для всех Minecraft Java Edition серверов устанавливается Java 11 или 16, в зависимости от устанавливаемой версии игры. Поскольку, начиная с версии 1.17, игра требует Java 16 для работы, в то время как старые версии (например, 1.12.2) её не поддерживают, клиенты могут сталкиваться с подобными ошибками при запуске серверов:

```log
Error: LinkageError occurred while loading main class net.minecraft.server.Main 
 java.lang.UnsupportedClassVersionError: net/minecraft/server/Main has been compiled by a more recent version of the Java Runtime (class file version 60.0), this version of the Java Runtime only recognizes class file versions up to 55.0
```

Конкретно эта ошибка вызвана тем, что сервер, не поддерживающий версии Java до 16, запускается с Java 11. Владельцы серверов с Forge могут сталкиваться с тем, что их сервера не запускаются, в самом начале выдавая такую ошибку:

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

Эта ошибка тоже вызвана использованием неподдерживаемой версии Java. Старые версии Forge поддерживают только Java 8 и не умеют работать с новыми механизмами загрузки классов, введёнными в Java 9. В обоих случаях возникает необходимость установить другую версию Java. Клиенты в большинстве случаев могут сделать это сами.

!> Сервера на хостинге запускаются в Docker контейнерах, что позволяет изолировать их друг от друга и относительно легко создать нужную среду для сервера. В Docker эта среда создаётся из так называемого **образа**. Соответственно, для изменения версии Java в контейнере, нужно изменить Docker образ.

## Инструкция
1. Перейдите во вкладку "Запуск" в панели управления сервером

![Вкладка "Запуск"](/images/guides/change-java/page-start.png)

2. В разделе **Docker образ** выберите нужную версию. 
- Java 8 - `ghcr.io/pterodactyl/yolks:java_8`
- Java 11 - `ghcr.io/pterodactyl/yolks:java_11`
- Java 16 - `ghcr.io/pterodactyl/yolks:java_16`
- Java 17 - `ghcr.io/pterodactyl/yolks:java_17`

Всё, версия Java изменена. Для применения изменений необходимо перезапустить сервер.

## Возможные проблемы

### Не могу выбрать образ
На некоторых серверах, особенно старых, вы можете столкнуться с тем, что выбрать образ нельзя:

![Нельзя изменить образ](/images/guides/change-java/cant-change-docker-image.png)

В таких ситуациях просто обратитесь в техническую поддержку, мы установим нужную версию Java.
