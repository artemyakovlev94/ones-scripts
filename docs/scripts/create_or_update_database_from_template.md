# `scripts/create_or_update_database_from_template.os`

Пользовательская точка входа для создания базы worktree копированием существующего файла `1Cv8.1CD` и последующего обновления базы.

## Используемые параметры

Контракт совпадает со скриптом [`create_or_update_database.os`](create_or_update_database.md):

- `--worktree-name` — обязательное имя worktree;
- `--worktree-path` — обязательный путь к worktree;
- `--db-name` — необязательное имя базы в `ibases.v8i`; по умолчанию используется имя worktree;
- `--db-path` — необязательный путь к целевой базе; по умолчанию используется `ONE_C_BASES_PATH\<worktree-name>`;
- повторяемые пары `--extension-name` и `--extension-path` — подключаемые расширения.

## Переменные окружения

Используются те же переменные, что и для `create_or_update_database.os`, а также обязательная `ONE_C_BASES_TEMPLATE` — каталог шаблонной базы с файлом `1Cv8.1CD`.

`PLAY_COMPLETION_SOUND` управляет звуковым уведомлением об успехе или ошибке.

## Запуск

```powershell
oscript scripts\create_or_update_database_from_template.os `
  --worktree-name "DEV-12345" `
  --worktree-path "D:\git\DEV-12345"
```

## Результат

Если целевая база отсутствовала, в её каталог скопирован исходный `1Cv8.1CD`. База обновлена исходниками worktree, расширения загружены, запись в `ibases.v8i` обеспечена, клиент 1С запущен.

Подробная настройка, команда запуска и описание результата приведены в [руководстве пользователя](../user-guide/create_or_update_database_from_template.md).
