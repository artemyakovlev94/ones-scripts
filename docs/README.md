# Документация скриптов

Документация организована по структуре исходного кода.

## Общие соглашения

- [Входные параметры пользовательских скриптов](script-parameters.md).
- [Переменные окружения](environment-variables.md).

## Библиотеки

- [`src/lib/archive.os`](src/lib/archive.md) — распаковка ZIP-архивов.
- [`src/lib/config.os`](src/lib/config.md) — чтение JSON-конфигурации проекта.
- [`src/lib/download.os`](src/lib/download.md) — скачивание файлов по HTTP и HTTPS.
- [`src/lib/env.os`](src/lib/env.md) — загрузка переменных из `config/.env`.
- [`src/lib/files.os`](src/lib/files.md) — поиск, создание каталогов и копирование файлов.

## Workflows

- [`src/workflows/download_cfe_bsp.os`](src/workflows/download_cfe_bsp.md) — скачивание и сохранение CFE BSP.

## Пользовательские скрипты

- [`scripts/download_cfe_bsp.os`](scripts/download_cfe_bsp.md) — пользовательская точка входа для загрузки CFE BSP.
