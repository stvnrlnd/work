---
title: 2493-upgrade-shipping
type: work-item
item_type: task
project: houseplans.net
status: in-review
created: 2026-04-14
updated:
due: 2026-04-20
url: https://trello.com/c/vnjBHSoH/2493-upgrade-shipping
assignee: Steven R.
---

# 2493-upgrade-shipping

## Description

Let’s fix the cart, which should determine the shipping type automatically. For cases where there is more than one package line item, you will want to ignore the ‘fulfilled’ line item and use the one without a description (or the one marked ‘upgrade’. If there is only one (and it is ‘fulfilled’ you will use that).

---

On order # 2511201055767 the shipping charges and shipping type were carried over from the original order (expedited shipping for sets), but the upgrade was for a PDF and didn’t need any shipping charges. We need to prompt the user to double check the shipping when creating an upgrade.

## Notes

