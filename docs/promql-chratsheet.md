# PromQL Cheatsheet

## Базовые метрики
- `up` — статус всех таргетов (1 = UP, 0 = DOWN)
- `up{job="node"}` — только ноды

## CPU
- Загрузка CPU в %: `100 - (avg by(instance)(rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)`

## RAM
- Использование RAM в %: `(1 - node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes) * 100`

## Диск
- Свободное место (байты): `node_filesystem_avail_bytes{mountpoint="/"}`

## Сеть
- Входящий трафик: `rate(node_network_receive_bytes_total[5m])`
