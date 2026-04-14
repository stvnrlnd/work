---
title: 2582-elastic-server-for-analytics
type: work-item
item_type: task
project: houseplans.net
status: done
created: 2026-04-14
updated:
due: 2026-03-10
url: https://trello.com/c/T2DGVMqq/2582-elastic-server-for-analytics
assignee: Shawn K.
---

# 2582-elastic-server-for-analytics

## Description

We will need to update the .envrc on PROD

```
SetEnv ELASTIC_ANALYTICS_PASSWORD    SAME AS elastic-01
SetEnv ELASTIC_ANALYTICS_CA_PATH     /var/www/houseplans.net/certs/analytics_ca.crt
SetEnv ELASTIC_ANALYTICS_HOSTNAME    https://10.108.0.26:9200
```

## Notes

