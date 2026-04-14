---
title: "BUG — Similar Plans Slider"
type: task
task_type: bug
source: abhp
project: abhp
status: ready
created: 2026-04-14
updated: 2026-04-14
due:
trello_id: 2455
---

## Description

Add additional scope for 'Similar Plans' algorithm that looks for matches using the plan's secondary styles.

---

My guess is because of the way our algorithm pulls in plans, there weren't other plans that fit the exact "similar" plans, is this the case or is there a bug? This is not a great experience, especially with the similar plans push up - it would only show one plan

If you look at some larger plans, like 5032-00260, there is just no similar plans slider at all.

It seems like there should be some sort of fallback if something doesn't meet our exact "similar criteria", then maybe expand the criteria, so the similar plans slider is always populated.

## Notes

