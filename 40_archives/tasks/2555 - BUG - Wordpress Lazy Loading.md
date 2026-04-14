---
title: "BUG — WordPress Lazy Loading"
type: task
task_type: bug
source: abhp
project: abhp
status: ready
created: 2026-04-14
updated: 2026-04-14
due:
trello_id: 2555
---

## Description

The last 9 images in [this blog](https://www.houseplans.net/news/2025-spotlight-your-most-loved-home-designs-of-the-year/) are all small, and the first 3 are larger, even though they are all set to the same "large" thumbnail size in wordpress. In safari, they are all showing large, but in Chrome, they show as the first 3 large and the rest of them small. We tried changing them all to medium, and the 2nd and 3rd images remained large.

From Taylor: It appears to be the effect of Wordpress's auto lazy loading, which Chrome doesn't interpret correctly.  If you can create a bug card we can figure out a work-around

![](https://trello.com/1/cards/69542b4bc0a222f888f86c45/attachments/69542c11936f0de739aba326/download/image.png "Attachment")

## Notes

