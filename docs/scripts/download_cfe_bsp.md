# `scripts/download_cfe_bsp.os`

Пользовательский скрипт для скачивания актуального CFE BSP из ZIP-архива.

## Запуск

Из корня проекта:

```powershell
oscript scripts\download_cfe_bsp.os
```

## Переменные окружения

Значения читаются из `config/.env` до подключения workflow.

- `CFE_ARCHIVE_URL` — URL ZIP-архива.
- `CFE_TARGET_DIRECTORY` — каталог для результирующего файла.
- `CFE_TARGET_FILE_NAME` — конечное имя с расширением `.cfe`.

После успешного выполнения в указанном каталоге находится загруженный CFE под заданным именем.
