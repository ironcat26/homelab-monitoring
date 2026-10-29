# Runbook: DiskFull

## Симптом
На почту приходит алерт `[FIRING] HighDiskUsage` или `[FIRING] DiskWillFillIn4Hours`.

## Диагностика
1. Зайти на сервер по SSH.
2. Проверить свободное место: `df -h`.
3. Найти самые большие папки: `sudo du -sh /* 2>/dev/null | sort -hr | head -n 10`.

## Решение
1. Очистить старые логи системы: `sudo journalctl --vacuum-size=200M`.
2. Удалить старые пакеты: `sudo apt autoremove -y && sudo apt clean`.
3. Удалить старые архивы (если есть): `sudo rm -rf /tmp/*.tar.gz`.
4. Если это база данных (Prometheus) — настроить retention (срок хранения).

## Эскалация
Если диск заполнен более чем на 95% — сообщить старшему инженеру немедленно.
