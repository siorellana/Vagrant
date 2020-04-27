# Consultas útiles de Prometheus

* CPU por modos

`avg by (mode) (irate(node_cpu_seconds_total[30s])*100)`

* CPU por instancia

`avg by (instance) (irate(node_cpu_seconds_total{mode="user"}[30s])*100)`
