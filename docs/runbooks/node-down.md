# Runbook: NodeDown

## Симптом
На почту приходит письмо с темой "Alertmanager Notification" и статусом FIRING.

## Диагностика
1. Проверить доступность сервера: `ping 10.10.10.21`
2. Проверить статус сервиса: `ssh cat@10.10.10.21 "sudo systemctl status node_exporter"`

## Решение
1. Перезапустить сервис: `ssh cat@10.10.10.21 "sudo systemctl start node_exporter"`
2. Если не помогло — проверить логи: `ssh cat@10.10.10.21 "sudo journalctl -u node_exporter -n 50"`

## Эскалация
Если сервер не отвечает более 5 минут — сообщить старшему инженеру.
