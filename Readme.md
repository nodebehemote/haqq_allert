
### Setup 
- Change YOUR_BOT_TOKEN and YOUR_GROUP_CHAT_ID in alertmanager/config.yml
Run using bash  
- docker-compose up -d --build


### If you want change your node address
- Set HOST environment vairable

### Dashboards 
For grafana dashboards, two exampls in dahsboards folder, which you can load using  original tutorial 
https://grafana.com/docs/grafana/latest/dashboards/manage-dashboards/

### Customize

You can customize alerts for your node via prometheus/alert.yml using 
Detail docs is here: https://prometheus.io/docs/prometheus/latest/configuration/alerting_rules/

This repository holds an example which send an alert to telegram chat if go compiler using more than 10 mb of RAM 

```yaml 
- name: haqq_node_group
  rules:
  - alert: ContainerFailing
    expr: 'go_memstats_gc_sys_bytes >= 10'
    for: 1m
    labels:
      severity: error
    annotations:
      summary: "{{ $labels.instance }} is mem overflow"
      description: "Alarm to much memory"
```

For another parameters you can go to : http:// {YOURHOST/localhost}:9110/graph where you can find a lot of different metrics which scraped from your node
