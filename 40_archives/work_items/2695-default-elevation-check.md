---
title: 2695-default-elevation-check
type: work-item
item_type: task
project: houseplans.net
status: ready
created: 2026-04-14
updated:
due: 2026-04-21
url: https://trello.com/c/gZflPb9D/2695-default-elevation-check
assignee: Steven R.
---

# 2695-default-elevation-check

## Description

If a plan does not have a default elevation, an empty placeholder will be shown in the cart and elsewhere (but this is undesirable). We need to add a default elevation check to our publishing check on the order edit page.

Ideally we should also update our code to use the next available elevation if the default is not marked. The cart is one such place where it only looks for a default elevation and if one isn’t found it just shows a placeholder.

## Notes

