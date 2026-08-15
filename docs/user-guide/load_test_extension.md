# Загрузка тестового расширения

Скрипт `scripts/load_test_extension.os` собирает расширение из каталога, заданного `WORKTREE_PATH_CFE_TEST`, и загружает его в существующую файловую базу. Другие операции с базой не выполняются.

## Требования

- Windows;
- OneScript с доступной командой `oscript`;
- Vanessa Automation с доступной командой `vrunner`;
- установленная платформа 1С версии и разрядности из окружения;
- наличие `ibcmd.exe` соответствующей платформы;
- существующий файл `1Cv8.1CD` в каталоге базы;
- права на чтение исходников расширения и запись в корневую `.temp`.

## Зависимости

Скрипт использует `src/lib/env.os`, `src/lib/arguments.os` и `src/workflows/create_or_update_database.os`. Все внутренние зависимости входят в репозиторий.

## Что настроить

В `config/.env`, созданном по образцу `config/.env.example`, задайте:

```dotenv
ONE_C_PLATFORM_VERSION=8.3.27.1916
ONE_C_PLATFORM_BITNESS=x64
SHOW_COMMAND_WINDOWS=true
ONE_C_BASES_PATH=D:\db
ONE_C_INFOBASE_USER=Administrator
ONE_C_INFOBASE_PASSWORD=
WORKTREE_PATH_CFE_TEST=src\tests
```

`WORKTREE_PATH_CFE_TEST` задаётся относительно `--worktree-path`. `ONE_C_BASES_PATH` используется только при отсутствии `--db-path`.

`SHOW_COMMAND_WINDOWS=false` скрывает окна внешних команд; при `true` окна отображаются.

## Как запустить

С явно указанной базой:

```powershell
oscript scripts\load_test_extension.os `
  --worktree-name "DEV-12345" `
  --worktree-path "D:\git\DEV-12345" `
  --db-path "D:\db\DEV-12345"
```

Если база находится в `ONE_C_BASES_PATH\DEV-12345`, параметр `--db-path` можно не передавать:

```powershell
oscript scripts\load_test_extension.os `
  --worktree-name "DEV-12345" `
  --worktree-path "D:\git\DEV-12345"
```

## Что делает скрипт

1. Проверяет обязательные параметры и настройки.
2. Проверяет наличие `1Cv8.1CD` в каталоге базы. Отсутствующая база не создаётся.
3. Читает имя расширения из его `Configuration.xml`.
4. Собирает временный CFE в корневой `.temp`.
5. Загружает CFE в базу и отключает безопасный режим, защиту от опасных действий и использование в распределённой базе.
6. Удаляет временный CFE, в том числе при ошибке обработки.

Скрипт не загружает основную конфигурацию, не изменяет `ibases.v8i` и не запускает клиент 1С.

## Результат

Тестовое расширение загружено в указанную существующую базу. Постоянные файлы вне базы не создаются.

[Вернуться к оглавлению](README.md)
