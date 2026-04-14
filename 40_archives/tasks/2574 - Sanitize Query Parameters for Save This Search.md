---
title: Sanitize Query Parameters for Save This Search
type: task
task_type: security
source: abhp
project: abhp
status: ready
created: 2026-04-14
updated: 2026-04-14
due:
trello_id: 2574
---

## Description

The Save This Search feature stores the current search url in the database, but this often contains advertising parameters (utm_source, etc) and is also a security vulnerability.

We need to rebuild the query using validated search paramater data only before storing the url encoded string.

## Notes

