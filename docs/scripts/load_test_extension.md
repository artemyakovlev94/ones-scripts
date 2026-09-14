# `scripts/load_test_extension.os`

Пользовательская точка входа для прямой загрузки тестового расширения из исходников worktree в существующую файловую базу 1С.

## Используемые параметры

- `--worktree-name` — обязательное имя worktree;
- `--worktree-path` — обязательный путь к worktree;
- `--db-path` — необязательный путь к существующей базе; по умолчанию используется `ONE_C_BASES_PATH\<worktree-name>`.

Остальные параметры общего контракта скрипт не использует.

## Переменные окружения

- `ONE_C_PLATFORM_VERSION`;
- `ONE_C_PLATFORM_BITNESS`;
- `SHOW_COMMAND_WINDOWS`;
- `PLAY_COMPLETION_SOUND`;
- `ONE_C_BASES_PATH` — требуется, если не передан `--db-path`;
- `ONE_C_INFOBASE_USER`;
- `ONE_C_INFOBASE_PASSWORD`;
- `WORKTREE_PATH_CFE_TEST`.

## Запуск

```powershell
oscript scripts\load_test_extension.os `
  --worktree-name "DEV-12345" `
  --worktree-path "D:\git\DEV-12345" `
  --db-path "D:\db\DEV-12345"
```

## Результат

Тестовое расширение загружено напрямую из исходников в существующую базу и настроено без ограничений. Основная конфигурация и `ibases.v8i` не изменяются, клиент 1С не запускается.

Подробности приведены в [руководстве пользователя](../user-guide/load_test_extension.md).
