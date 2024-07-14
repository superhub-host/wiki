---
title: Смена версии Java (JDK)
description: Инструкция по изменению версии Java на сервере в панели.
---

По умолчанию на нашем хостинге для всех Minecraft серверов устанавливается Java 21. Дело в том что зачастую клиенты используют новейшие версии игры, по этому если вы используете более старую версию вы можете сталкиваться с подобными ошибками при запуске серверов:

```log
Error: LinkageError occurred while loading main class net.minecraft.server.Main 
 java.lang.UnsupportedClassVersionError: net/minecraft/server/Main has been compiled by a more recent version of the Java Runtime (class file version 60.0), this version of the Java Runtime only recognizes class file versions up to 55.0
```
```log
Minecraft 1.19 requires running the server with Java 17 or above. Download Java 17 (or above) from https://adoptium.net/
```

Конкретно данные ошибки говорят о том, что ваш сервер не поддерживает текущую версию java и вам нужно изменить её на нужную вам:

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
- Java 18 - `ghcr.io/pterodactyl/yolks:java_18`
- Java 19 - `ghcr.io/pterodactyl/yolks:java_19`
- Java 21 - `ghcr.io/pterodactyl/yolks:java_21`

P.S. open J9 - это уникальная обработка сделанная под java для изменений потребовательности памяти - оно значительно уменьшает вес потребления оперативной памяти на вашем сервере. Но возможно некоторые плагины и моды - не смогут работать с данной структурой. Какую использовать можете решить самостоятельно, но советуем использовать классический вариант.

Всё, версия Java изменена. Для применения изменений необходимо перезапустить сервер.

## Какие же всё таки версии java нужно использовать и на какой версии

### spigot paper и аналоги:

- До версии майнкрафт 1.15.* - `требуется 8 java или 11 java в зависимости от плагинов`
- Версии 1.16.* и 1.17.* - `используйте 16 java`
- Версии 1.18.* - 1.20.*  - `требуется 17 и выше в зависимости от плагинов`
- Версия 1.21.* - `Используется 21 java`

### forge или fabric:

До версии 1.16.5 (java 8)  
версии выше, зависят от установленных на них плагинах, возможно включение на 8 java, но бывали случаи когда сервер запускался только на 19 - Вам нужно перебирать java - перезапуская сервер и проверяя ошибки в консоли. К сожалению более точную информацию дать не могу.

## Возможные проблемы

### Не могу выбрать образ
На некоторых серверах, особенно старых, вы можете столкнуться с тем, что выбрать образ нельзя:

![Нельзя изменить образ](/images/guides/change-java/cant-change-docker-image.png)

В таких ситуациях просто обратитесь в техническую поддержку, мы установим нужную версию Java.

