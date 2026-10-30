---
title: Управление игровыми правилами в Minecraft
description: Как менять game rules, gamerule и основные игровые правила Minecraft Java и Bedrock.
---

Игровые правила Minecraft, или «game rules», управляют поведением мира: выпадением предметов, сменой дня и ночи, уроном от падения, сохранением инвентаря после смерти и другими механиками. Их меняют командой `gamerule`.

## Что нужно

Чтобы изменить игровые правила на сервере, нужен доступ к консоли или права оператора.

Варианты:

- выполнить команду в консоли панели управления;
- зайти в игру с OP-правами (для этого понадобится прописать в консоли `op ваш_ник`) и выполнить команду в чате.

Если вводишь команду в игре, нужен `/` в начале. Если вводишь команду в консоли панели, `/` обычно не нужен.

?> Для удалённого Bedrock-сервера используй команды в консоли или игровом чате с правами оператора. Доступность настроек мира в меню игры зависит от способа запуска сервера.

## Значения правил

Названия правил зависят от редакции и версии игры. Начиная с Java Edition 1.21.11 они изменились: например, `keepInventory` стало `minecraft:keep_inventory`. Это описано в [примечаниях к выпуску](https://www.minecraft.net/en-us/article/minecraft-java-edition-1-21-11). В Bedrock используются прежние названия.

Большинство правил принимают `true` или `false`. Следующие примеры предназначены для Java Edition 1.21.11 и новее; для других версий используй названия из таблиц ниже.

Пример включения сохранения инвентаря после смерти:

```text
gamerule minecraft:keep_inventory true
```

Пример отключения разрушения мира мобами:

```text
gamerule minecraft:mob_griefing false
```

Некоторые правила принимают число. Например, `minecraft:random_tick_speed` управляет скоростью случайных тиков, а `minecraft:players_sleeping_percentage` — процентом игроков, которые должны лечь спать для пропуска ночи.

Чтобы посмотреть текущее значение правила, введи команду без значения:

```text
gamerule minecraft:keep_inventory
```

## Java Edition

Выбирай название из столбца своей версии. Наличие правила в старых выпусках и полный список проверяй в [документации](https://minecraft.wiki/w/Game_rule). В игровом чате можно ввести `/gamerule ` и нажать Tab, чтобы увидеть доступные имена.

| Java 1.21.11 и новее | Java до 1.21.11 | Значения | Что делает |
| --- | --- | --- | --- |
| `minecraft:keep_inventory` | `keepInventory` | `true` или `false` | Сохраняет инвентарь и опыт после смерти. |
| `minecraft:mob_griefing` | `mobGriefing` | `true` или `false` | Разрешает мобам менять мир: взрывы криперов, подбор предметов, действия эндерменов и другие эффекты. |
| `minecraft:advance_time` | `doDaylightCycle` | `true` или `false` | Включает или выключает смену дня и ночи. |
| `minecraft:advance_weather` | `doWeatherCycle` | `true` или `false` | Включает или выключает естественную смену погоды. |
| `minecraft:spawn_mobs` | `doMobSpawning` | `true` или `false` | Разрешает естественный спавн мобов. Спавнеры это правило обычно не отключает. |
| `minecraft:mob_drops` | `doMobLoot` | `true` или `false` | Управляет выпадением предметов и опыта с мобов. |
| `minecraft:block_drops` | `doTileDrops` | `true` или `false` | Управляет выпадением блоков при разрушении. |
| `minecraft:fire_spread_radius_around_player` | `doFireTick` | В новых версиях — число; в старых — `true` или `false` | В новых версиях задаёт радиус распространения огня вокруг игрока: `0` отключает распространение, `-1` снимает ограничение по близости игроков. |
| `minecraft:fall_damage` | `fallDamage` | `true` или `false` | Включает или выключает урон от падения. |
| `minecraft:fire_damage` | `fireDamage` | `true` или `false` | Включает или выключает урон от огня и лавы. |
| `minecraft:drowning_damage` | `drowningDamage` | `true` или `false` | Включает или выключает урон от утопления. |
| `minecraft:freeze_damage` | `freezeDamage` | `true` или `false` | Включает или выключает урон от замерзания в рыхлом снегу. |
| `minecraft:natural_health_regeneration` | `naturalRegeneration` | `true` или `false` | Управляет естественным восстановлением здоровья при сытости. |
| `minecraft:show_death_messages` | `showDeathMessages` | `true` или `false` | Показывает или скрывает сообщения о смерти игроков. |
| `minecraft:show_advancement_messages` | `announceAdvancements` | `true` или `false` | Показывает или скрывает сообщения о достижениях в чате. |
| `minecraft:players_sleeping_percentage` | `playersSleepingPercentage` | число | Процент игроков, которые должны спать, чтобы пропустить ночь. |
| `minecraft:random_tick_speed` | `randomTickSpeed` | число | Скорость случайных тиков: рост растений, листва, распространение некоторых блоков. |
| `minecraft:respawn_radius` | `spawnRadius` | число | Радиус случайного появления игроков вокруг точки спавна мира. |
| `minecraft:max_entity_cramming` | `maxEntityCramming` | число | Сколько сущностей может находиться в одном месте до получения урона от тесноты. |
| `minecraft:reduced_debug_info` | `reducedDebugInfo` | `true` или `false` | Скрывает часть информации на экране отладки F3. |

## Bedrock Edition

В Minecraft: Bedrock Edition часть правил совпадает с Java Edition, а часть существует только в Bedrock. Названия правил в подсказках Bedrock могут отображаться в нижнем регистре, но обычно команда не чувствительна к регистру.

| Правило | Значения | Что делает |
| --- | --- | --- |
| `keepInventory` | `true` или `false` | Сохраняет инвентарь после смерти. |
| `mobGriefing` | `true` или `false` | Разрешает мобам менять блоки и взаимодействовать с миром. |
| `doDaylightCycle` | `true` или `false` | Управляет сменой дня и ночи. |
| `doWeatherCycle` | `true` или `false` | Управляет естественной сменой погоды. |
| `doMobSpawning` | `true` или `false` | Разрешает естественный спавн мобов. |
| `doMobLoot` | `true` или `false` | Управляет выпадением предметов и опыта с мобов. |
| `doTileDrops` | `true` или `false` | Управляет выпадением блоков. |
| `doFireTick` | `true` или `false` | Разрешает распространение огня. |
| `fallDamage` | `true` или `false` | Включает или выключает урон от падения. |
| `fireDamage` | `true` или `false` | Включает или выключает урон от огня. |
| `drowningDamage` | `true` или `false` | Включает или выключает урон от утопления. |
| `naturalRegeneration` | `true` или `false` | Управляет естественным восстановлением здоровья. |
| `showCoordinates` | `true` или `false` | Показывает координаты игрока на экране. |
| `showDeathMessages` | `true` или `false` | Показывает сообщения о смерти игроков. |
| `pvp` | `true` или `false` | Включает или выключает урон между игроками. |
| `tntExplodes` | `true` или `false` | Разрешает или запрещает взрывы TNT. |
| `recipesUnlock` | `true` или `false` | Управляет разблокировкой рецептов. |
| `playersSleepingPercentage` | число | Процент игроков, которые должны спать для пропуска ночи. |
| `randomTickSpeed` | число | Скорость случайных тиков мира. |
| `spawnRadius` | число | Радиус появления игроков вокруг спавна мира. |

## Распространённые ошибки

### Unknown or incomplete command

Ошибка:

```text
Unknown or incomplete command
```

Обычно означает, что команда введена с ошибкой, правило не существует в этой версии Minecraft или ты вводишь `/gamerule` со слэшем в консоли, где слэш не нужен.

### Нет прав

Если команда не выполняется в игре, проверь OP-права. Выдать права оператора можно через консоль командой:

```text
op НикИгрока
```

Подробнее о правах написано в статье [«Права на сервере Minecraft»](/guides/minecraft/server-permissions).

### Правило не работает

Проверь, что правило есть именно в твоей версии и редакции Minecraft. Некоторые правила доступны только в Java Edition, другие — только в Bedrock Edition. Если сервер модовый или работает через плагины, поведение правила также может изменяться дополнениями.

### Слишком большой randomTickSpeed

Большое значение `randomTickSpeed` может резко нагрузить сервер: растения, листва и другие блоки начнут обновляться слишком часто. Если сервер начал лагать после изменения правила, верни обычное значение.

Для Java Edition 1.21.11 и новее стандартное значение:

```text
gamerule minecraft:random_tick_speed 3
```

В Java Edition до 1.21.11 используй `gamerule randomTickSpeed 3`.

Для Bedrock Edition стандартное значение:

```text
gamerule randomTickSpeed 1
```
