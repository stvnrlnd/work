---
title: 2674-xtrabackup-config
type: work-item
item_type: task
project: houseplans.net
status: ready
created: 2026-04-21
updated:
due:
assignee:
url: https://trello.com/c/5b6uxVmp/2674-xtrabackup-config
---

# 2674-xtrabackup-config

## Description

Update the staging ‘fast’ backup pipeline script (xtrabackup) so that it only keeps the most recent backup and removes the others.

Take one Xtrabackup snapshot on production once every 6 hours. (at 12 and 6 EST), and keep 24 hours of backups.

Include staging backup in Bitbucket pipeline ‘staging-build’ CRON.

## Notes

