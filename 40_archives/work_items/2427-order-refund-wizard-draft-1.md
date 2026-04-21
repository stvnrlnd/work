---
title: 2427-order-refund-wizard-draft-1
type: work-item
item_type: task
project: houseplans.net
status: ready
created: 2026-04-21
updated:
due:
url: https://trello.com/c/4XofYfr7/2427-order-refund-wizard-draft-1
---

# 2427-order-refund-wizard-draft-1

## Description

This task creates a user interface for issuing refunds on individual line items and whole orders. It will give the employee the option to refund a credit card and have that automatically processed by Braintree, or to issue the user a store credit.

The user interface will give the option to process a refund without using the cart/checkout system for orders with negative totals, but will still produce order receipts like all other orders/upgrades.

When an employee creates an upgrade and it results in an order total that is a _**zero or negative amount**_, add a REFUND button next to the PAY button. The refund button should initialize a pop-up form that ask whether we want the refund to go back to the original card or be stored as a store credit. It will also need a few other fields similar to the Add Credit form available on the Admin Customer Profile page. The credit should associate the order it came from automatically.

## Notes

