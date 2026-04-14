---
title: Order Revisions Before Releasing to Designer
type: task
task_type: feature
source: abhp
project: abhp
status: ready
created: 2026-04-14
updated: 2026-04-14
due:
trello_id: 200
---

## Description

Before an order is released to the designer(s), we want to have the ability to reset the order and make changes if necessary. To accomplish this, we want a button that deletes the current order deliverables and the email receipt stored in the database so that they can be regenerated with any changes made by an admin user. We also want to log the changes and allow the admin user to process the order when ready. Until the order is processed again, the order needs to indicate that it is in a reprocessing state.

---

~~Background Info: Order not added to Designer portal until it is pushed through.~~

~~New features:~~

- ~~Changes to the order will require a new customer and designer receipt emailed out. This can happen before or after "approval" but his task is only concerned with "before approval (before emails sent to the designer).~~

- ~~Changes to the order may require changes to deliverables, shipping, discounts, payments, etc.~~

- ~~We need to log changes to the order history table to document what was changed, why, by whom, and when.~~

- ~~We should lock changes to the order for all but approved employees.~~


**~~This task does not require any payment processing - this will be done manually by employees.~~**

~~Changes AFTER an order is released to the designer require a different set of procedures and checks, especially for multi-designer orders.~~ **~~This task only addresses the "not released to designer" stage of the order.~~**

## Notes

