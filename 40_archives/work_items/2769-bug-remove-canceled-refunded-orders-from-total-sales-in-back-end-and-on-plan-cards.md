---
title: 2769-bug-remove-canceled-refunded-orders-from-total-sales-in-back-end-and-on-plan-cards
type: work-item
item_type: task
project: houseplans.net
status: ready
created: 2026-04-21
updated:
due:
url: https://trello.com/c/0uxvpZmq/2769-bug-remove-canceled-refunded-orders-from-total-sales-in-back-end-and-on-plan-cards
---

# 2769-bug-remove-canceled-refunded-orders-from-total-sales-in-back-end-and-on-plan-cards

## Description

It seems that canceled/refunded orders may still show in the back end & on the plan card/total sales. Example: 4534-00159 shows 4 sales here: [https://www.houseplans.net/edit/houseplans/index.php?designer_id=563125337](https://www.houseplans.net/edit/houseplans/index.php?designer_id=563125337)

& on the plan card:

![](https://trello.com/1/cards/69df8cbb4df9738f1772a120/attachments/69df8d22eac287999afa65bf/previews/69df8d23eac287999afa65cf/download/image.webp "Attachment")

The plans by most sales reports only show 3, so it seems that canceled orders aren’t factored in there.

Order #2604131119083 was canceled & refunded, but it seems to still be counting as a sale. See [all orders](https://www.houseplans.net/edit/orders/index.php?action=search&order_id=&order_number=&plan_name=4534-00159&customer_name=&designer_id=&order_status=all&from_month=4&from_day=12&from_year=2025&to_month=4&to_day=15&to_year=2026) for that plan.

I noticed it because on 4/13, I knew we only had 1 sale for this plan, then it sold 3 times on 4/14, but one was to the same person (Chip Lynn), so I looked into it because his original mod order was refunded.

## Notes

