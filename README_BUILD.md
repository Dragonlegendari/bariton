# Gradle files for Baritone 1.21.11 Unofficial

## Что сделано:
Созданы все необходимые файлы для сборки Baritone под Minecraft 1.21.11 с Fabric Loader.

## Структура файлов:
```
/workspace
├── gradle.properties              # Настройки версий (MC 1.21.11, Yarn mappings, Fabric Loader)
├── build.gradle                   # Конфигурация сборки с Fabric Loom
├── settings.gradle                # Настройки репозиториев
├── gradlew.bat                    # Скрипт запуска для Windows
├── gradle/wrapper/
│   └── gradle-wrapper.properties  # Настройки Gradle Wrapper (8.10)
└── src/main/resources/
    ├── fabric.mod.json            # Манифест мода для Fabric
    └── baritone.mixins.json       # Конфигурация Mixin'ов
```

## Инструкция по использованию:

### 1. Скопируй исходный код Baritone
Так как это только конфиги, тебе нужно скопировать весь Java-код из оригинального репозитория:
```bash
# В своей папке с проектом выполни:
git clone https://github.com/cabaletta/baritone.git temp-baritone
# Скопируй папку src из temp-baritone в /workspace (заменив существующую если есть)
# Или скопируй только нужные подмодули (baritone-fabric или аналогичный)
```

### 2. Проверь структуру проекта
Baritone имеет сложную структуру с несколькими подпроектами. Убедись, что:
- Основной код находится в `src/main/java/baritone/`
- Ресурсы в `src/main/resources/`
- Файл `fabric.mod.json` должен быть в resources

### 3. Обнови зависимости
Перед сборкой проверь актуальные версии на:
- **Yarn Mappings**: https://fabricmc.net/develop/ (найди последний build для 1.21.11)
- **Fabric API**: https://modrinth.com/mod/fabric-api/versions (если используется)

Открой `gradle.properties` и замени:
```properties
yarn_mappings=1.21.11+build.1  # <- поставь актуальный build
```

### 4. Сборка
```bash
# Убедись что установлен JDK 21
java -version

# Запусти сборку
gradlew.bat clean build
# или
./gradlew clean build (на Linux/Mac)
```

### 5. Исправление ошибок компиляции
После первого запуска ты получишь ошибки компиляции — это нормально. 
Mojang меняют названия методов/полей между версиями. Тебе нужно:

1. Смотреть ошибки в логе сборки
2. Использовать https://maven.fabricmc.net/ для поиска актуальных названий
3. Обновлять код в соответствии с новыми маппингами
4. Особое внимание удели Mixin'ам — сигнатуры методов могли измениться

## Важные замечания:
- **Java 21 обязательна** для MC 1.21+
- **Fabric Loom 1.9+** требуется для новых версий
- Баритон может использовать собственные маппинги вместо Yarn — проверь оригинальный репозиторий
- Возможно потребуется создать `LICENSE` файл

## Где искать помощь по исправлению кода:
1. Ошибки компиляции покажут какие классы/методы изменились
2. https://github.com/FabricMC/yarn — диффы маппингов между версиями
3. https://minecraft.wiki — changelog изменений игры

Удачи со сборкой! 🛠️
