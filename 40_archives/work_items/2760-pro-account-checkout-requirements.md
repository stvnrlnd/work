---
title: 2760-pro-account-checkout-requirements
type: work-item
item_type: task
project: houseplans.net
status: ready
created: 2026-04-21
updated:
due:
assignee: Shawn K.
url: https://trello.com/c/OoUf1vPl/2760-pro-account-checkout-requirements
---

# 2760-pro-account-checkout-requirements

## Description

If a Pro user account email address is used during checkout and the user is not signed in, the auth modal is opened with a message asking them to sign in.

If the user clears the form but tries to submit the page form without signing in (or changing the email address), we need to prevent the form submission and re-open the auth form again.

## Notes

