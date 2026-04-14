---
title: 2526-customer-receipt-delivery-delay-notices
type: work-item
item_type: task
project: houseplans.net
status: in-review
created: 2026-04-14
updated:
due: 2026-04-09
url: https://trello.com/c/jVvF5MS8/2526-customer-receipt-delivery-delay-notices
assignee: Steven R.
---

# 2526-customer-receipt-delivery-delay-notices

## Description

The DELIVERY DELAY notes in the floorplans_data table that show in the cart also need to show on the customer’s order receipt in the ‘About Your Order’ section. If the delay notice is plan specific and there are multiple plans, please include the plan number in the notice. These notes have start and end dates.

We also want to show any active CART notification in the notifications table in this section of the receipt. These entries also have start and end dates.

~~We only want to show one notification in the email and the cart when the scope is the same. If there are multiple notices that cover all plans (typically when there is one plan in the cart), prefer the one that has the most future end date.~~ THIS REQUIREMENT HAS BEEN REMOVED DUE TO COMPLEXITY.

---

We also need instruction in the CART notification area to let users know where this message will show.

![](https://trello.com/1/cards/6939dbc8c54617a760f97a63/attachments/69418bf7913fd34e406ff89e/download/image.png "Attachment")

---

Please also fix the bug where the CART notification shows in a separate block than the `floorplan_data` notes.

![](https://trello.com/1/cards/6939dbc8c54617a760f97a63/attachments/694187b6de8a165529659405/download/image.png "Attachment")

## Notes

