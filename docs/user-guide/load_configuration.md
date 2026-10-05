# Загрузка исходников конфигурации

Скрипт `scripts/load_configuration.os` загружает только исходники основной конфигурации в существующую файловую базу 1С и обновляет конфигурацию базы данных.

## Требования

- Windows;
- OneScript с доступной командой `oscript`;
- Vanessa Runner 3.x с доступной командой `vrunner`;
- установленная платформа 1С требуемой версии и разрядности;
- `ibcmd.exe` соответствующей платформы;
- существующий файл `1Cv8.1CD` в каталоге базы;
- доступ на чтение каталога исходников конфигурации и на изменение базы.

## Зависимости

Скрипт использует `src/lib/env.os`, `src/lib/arguments.os` и `src/workflows/create_or_update_database.os`. Все внутренние зависимости входят в репозиторий.

## Что настроить

В `config/.env`, созданном по образцу `config/.env.example`, задайте:

```dotenv
ONE_C_PLATFORM_VERSION=8.3.27.1916
ONE_C_PLATFORM_BITNESS=x64
SHOW_COMMAND_WINDOWS=true
PLAY_COMPLETION_SOUND=false
ONE_C_BASES_PATH=D:\db
ONE_C_INFOBASE_USER=Administrator
ONE_C_INFOBASE_PASSWORD=
REPOSITORY_PATH_CF=src\cf
```

`REPOSITORY_PATH_CF` задаётся относительно `--repo-path`. `ONE_C_BASES_PATH` используется только при отсутствии `--db-path`.

## Как запустить

С явно указанной базой:

```powershell
oscript scripts\load_configuration.os `
  --branch-name "DEV-12345" `
  --repo-path "E:\git\TB" `
  --db-path "D:\db\DEV-12345"
```

Если база расположена в `ONE_C_BASES_PATH\DEV-12345`, параметр `--db-path` можно не передавать:

```powershell
oscript scripts\load_configuration.os `
  --branch-name "DEV-12345" `
  --repo-path "E:\git\TB"
```

## Что делает скрипт

1. Проверяет обязательные параметры и настройки.
2. Проверяет наличие `<db-path>\1Cv8.1CD` и каталога исходников конфигурации.
3. Импортирует исходники через `ibcmd infobase config import` с авторизацией из окружения.
4. Обновляет конфигурацию базы данных через `vrunner infobase update --ibcmd`.

Скрипт не создаёт базу, не загружает расширения, не изменяет `ibases.v8i` и не запускает клиент 1С.

## Результат

Основная конфигурация указанной существующей базы обновлена из исходников ветки. Постоянные файлы вне базы не создаются.

[Вернуться к оглавлению](README.md)

Репозиторий определяется через Git из текущего каталога запуска (включая его подкаталоги). `--repo-path` задаёт другой каталог репозитория. Имя задачи берётся из текущей Git-ветки; `--branch-name` переопределяет имя базы и папки, не переключая ветку. Для detached HEAD и веток со специальными символами, например `feature/DEV-12345`, передайте `--branch-name DEV-12345`. Требуется Git в PATH. Старые параметры `--worktree-name` и `--worktree-path` заменены новыми.

Настройки путей: `REPOSITORY_PATH_CF` и `REPOSITORY_PATH_CFE_TEST` относительно корня репозитория. Пока новые значения не заданы, используются прежние `WORKTREE_PATH_CF` и `WORKTREE_PATH_CFE_TEST`. Рабочий `config/.env` пользователь обновляет самостоятельно.
