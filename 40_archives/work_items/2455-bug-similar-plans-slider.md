---
title: 2455-bug-similar-plans-slider
type: work-item
item_type: task
project: houseplans.net
status: done
created: 2026-04-14
updated:
due: 2026-02-24
url: https://trello.com/c/DaDN4kI5/2455-bug-similar-plans-slider
assignee: Andre R.
---

# 2455-bug-similar-plans-slider

## Description

Add additional scope for ‘Similar Plans' algorithm that expands the Sq Ft to include more plans.

---

My guess is because of the way our algorithm pulls in plans, there weren’t other plans that fit the exact “similar” plans, is this the case or is there a bug? This is not a great experience, especially with the similar plans push up - it would only show one plan

If you look at some larger plans, like 5032-00260, there is just no similar plans slider at all.

It seems like there should be some sort of fallback if something doesn’t meet our exact “similar criteria”, then maybe expand the criteria, so the similar plans slider is always populated.

## Notes

