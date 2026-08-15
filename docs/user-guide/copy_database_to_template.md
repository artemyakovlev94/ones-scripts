# Копирование базы в шаблон

Скрипт `scripts/copy_database_to_template.os` сохраняет файл существующей базы как шаблон для последующего создания баз.

## Требования

- Windows;
- OneScript с доступной командой `oscript`;
- существующий файл `1Cv8.1CD` в каталоге исходной базы;
- права на чтение исходного файла и запись в каталог шаблона.

Платформа 1С и Vanessa Automation для копирования не требуются.

## Зависимости

Скрипт использует `src/lib/env.os`, `src/lib/arguments.os`, `src/lib/files.os` и `src/workflows/copy_database_to_template.os`. Все зависимости входят в репозиторий.

## Что настроить

В `config/.env`, созданном по образцу `config/.env.example`, задайте:

```dotenv
ONE_C_BASES_TEMPLATE=D:\db\templatedb
PLAY_COMPLETION_SOUND=false
```

При `PLAY_COMPLETION_SOUND=true` после завершения воспроизводится системный звук успеха или ошибки.

## Как запустить

```powershell
oscript scripts\copy_database_to_template.os `
  --db-path "D:\db\DEV-12345"
```

`--db-path` указывает каталог базы, а не сам файл `1Cv8.1CD`.

## Что делает скрипт

1. Проверяет обязательный параметр `--db-path` и переменную `ONE_C_BASES_TEMPLATE`.
2. Проверяет наличие `<db-path>\1Cv8.1CD`.
3. Создаёт каталог `ONE_C_BASES_TEMPLATE`, если он отсутствует.
4. Если шаблон уже существует, сохраняет его как `1Cv8_1.1CD.bak`, а прежнюю первую копию — как `1Cv8_2.1CD.bak`.
5. Копирует исходный файл как `ONE_C_BASES_TEMPLATE\1Cv8.1CD`, заменяя существующий шаблон.

## Результат

В каталоге `ONE_C_BASES_TEMPLATE` находится актуальная копия файла базы и максимум две предыдущие версии: `1Cv8_1.1CD.bak` и `1Cv8_2.1CD.bak`. Исходная база не изменяется.

[Вернуться к оглавлению](README.md)
