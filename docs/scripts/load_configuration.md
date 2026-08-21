# `scripts/load_configuration.os`

Загружает исходники основной конфигурации в существующую файловую информационную базу 1С и обновляет конфигурацию базы данных. Расширения не устанавливаются, список `ibases.v8i` не изменяется, клиент 1С не запускается.

## Параметры

Скрипт использует параметры общего [входного контракта](../script-parameters.md):

- `--worktree-name` — обязательное имя worktree; также используется для вычисления пути базы при отсутствии `--db-path`;
- `--worktree-path` — обязательный путь к worktree;
- `--db-path` — необязательный путь к существующей файловой базе.

## Переменные окружения

- `ONE_C_PLATFORM_VERSION`;
- `ONE_C_PLATFORM_BITNESS`;
- `ONE_C_INFOBASE_USER`;
- `ONE_C_INFOBASE_PASSWORD` — может быть пустым;
- `WORKTREE_PATH_CF`;
- `ONE_C_BASES_PATH` — требуется, если не передан `--db-path`;
- `SHOW_COMMAND_WINDOWS` — необязательная, значение по умолчанию `true`;
- `PLAY_COMPLETION_SOUND` — необязательная, значение по умолчанию `false`.

## Запуск

```powershell
oscript scripts\load_configuration.os `
  --worktree-name "DEV-12345" `
  --worktree-path "D:\git\DEV-12345" `
  --db-path "D:\db\DEV-12345"
```

## Результат

Исходники из `<worktree-path>\<WORKTREE_PATH_CF>` импортированы в указанную существующую базу, а конфигурация базы данных обновлена. Подробная подготовка окружения описана в [руководстве пользователя](../user-guide/load_configuration.md).
