# Substrate-grafana-dashboard
## based on [polkadot metrics](https://grafana.com/grafana/dashboards/11171) dashboard

1. add to the substrate service: `--prometheus-external --prometheus-port ${PROMETHEUS_PORT}`
2. add job named `substrate_name` and `job:` name to `prometheus.yml`:
```
  - job_name: 'centrifuge'
    scrape_interval: 15s
    static_configs:
      - targets: ['135.181.21.55:9635']
        labels:
          host: "Validator(Sentry)_Name"
          job: "centrifuge"
```
3. import dashboard.json
4. add notification channels to `Block Sync Rate [5m]` and/or `Peers or Port UP` or `CPU/Memory/Disk` panels
5. if prometheus job is named not `centrifuge` (`plasm` for example) then go to Settings\Variables and change `job=~".*centrifuge.*"` to your job name

![screenshot](https://github.com/AGx10k/kusama-grafana-dashboard/blob/master/kusama-dashboard-screeenshot.PNG?raw=true)
