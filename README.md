# homelab-monitoring

Observability stack on Proxmox homelab.

## Stack
- Proxmox VE (hypervisor)
- 3× Ubuntu 22.04 LTS VMs
- Ansible (configuration management)
- Prometheus + Alertmanager + Grafana (planned)
## Architecture
- monitor (10.10.10.20) — control node, planned: Prometheus, Alertmanager, Grafana
- app (10.10.10.21) — monitored node, planned: node_exporter, nginx
- db (10.10.10.22) — monitored node, planned: node_exporter, PostgreSQL

## Deployment
\\\bash
cd ansible
ansible-playbook site.yml
\\\
