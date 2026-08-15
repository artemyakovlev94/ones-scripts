# Документация скриптов

Документация организована по структуре исходного кода.

## Пользовательские инструкции

- [Руководство пользователя](user-guide/README.md) — подготовка к запуску и оглавление инструкций для всех скриптов из `scripts/`.
- [Пользовательская инструкция по переменным окружения](user-guide/environment-variables.md).

## Общие соглашения

- [Входные параметры пользовательских скриптов](script-parameters.md).
- [Переменные окружения](environment-variables.md).

## Библиотеки

- [`src/lib/archive.os`](src/lib/archive.md) — распаковка ZIP-архивов.
- [`src/lib/config.os`](src/lib/config.md) — чтение JSON-конфигурации проекта.
- [`src/lib/download.os`](src/lib/download.md) — скачивание файлов по HTTP и HTTPS.
- [`src/lib/env.os`](src/lib/env.md) — загрузка переменных из `config/.env`.
- [`src/lib/files.os`](src/lib/files.md) — поиск, создание каталогов и копирование файлов.
- [`src/lib/arguments.os`](src/lib/arguments.md) — разбор стандартных именованных параметров скриптов.
- [`src/lib/ibases.os`](src/lib/ibases.md) — управление папками и файловыми базами в `ibases.v8i`.
- [`src/lib/process.os`](src/lib/process.md) — синхронный запуск внешних команд.
- [`src/lib/logger.os`](src/lib/logger.md) — вывод сообщений с датой и временем.
- [`src/lib/one_c_database.os`](src/lib/one_c_database.md) — операции платформы с файловой базой 1С.
- [`src/lib/one_c_extensions.os`](src/lib/one_c_extensions.md) — сборка, загрузка и настройка расширений 1С.

## Workflows

- [`src/workflows/download_cfe_bsp.os`](src/workflows/download_cfe_bsp.md) — скачивание и сохранение CFE BSP.
- [`src/workflows/create_or_update_database.os`](src/workflows/create_or_update_database.md) — создание или обновление файловой базы worktree.

## Пользовательские скрипты

- [`scripts/download_cfe_bsp.os`](scripts/download_cfe_bsp.md) — пользовательская точка входа для загрузки CFE BSP.
- [`scripts/create_or_update_database.os`](scripts/create_or_update_database.md) — пользовательская точка входа для создания, обновления и запуска базы worktree.
- [`scripts/create_or_update_database_from_template.os`](scripts/create_or_update_database_from_template.md) — создание или обновление базы worktree из файла существующей базы.
- [`scripts/load_test_extension.os`](scripts/load_test_extension.md) — сборка и загрузка тестового расширения в существующую базу.
