---
title: AI Tool for Detecting Features
type: task
task_type: feature
source: abhp
project: abhp
status: ready
created: 2026-04-14
updated: 2026-04-14
due:
trello_id: 2377
---

## Description

We want to build an AI tool that analyzes plan images and identifies features from a predefined list.

The list should be stored in a separate database table, and identify the image types that the feature might be found in (for customizing prompts).

The results should be stored in a database table that records which image the feature was seen in.

After all images for a plan are scanned, the entire collection of matching features should be listed in the plan administration area for review.

We will also want to include a plan scanning cron that runs against plans one at a time on a scheduled interval, starting with the most popular plans from our plan rank algorithm. Keeping track of which images have been scanned will also be useful when a scan is interrupted or needs to be restarted (or if new images are added).

Here is the list of features: [https://docs.google.com/document/d/1UjehRUckKjStG_lreR2z2mO1GMXUIK4dRDUvzKmuOjg/edit?usp=sharing](https://docs.google.com/document/d/1UjehRUckKjStG_lreR2z2mO1GMXUIK4dRDUvzKmuOjg/edit?usp=sharing)

---

Context: Previous discussion was in this card: [https://trello.com/c/pXzurUoc](https://trello.com/c/pXzurUoc)

## Notes

