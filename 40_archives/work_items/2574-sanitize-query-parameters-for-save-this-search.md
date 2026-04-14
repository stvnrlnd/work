---
title: 2574-sanitize-query-parameters-for-save-this-search
type: work-item
item_type: task
project: houseplans.net
status: done
created: 2026-04-14
updated:
due: 2026-03-31
url: https://trello.com/c/fvMGibOr/2574-sanitize-query-parameters-for-save-this-search
assignee: Steven R.
---

# 2574-sanitize-query-parameters-for-save-this-search

## Description

The Save This Search feature stores the current search url in the database, but this often contains advertising parameters (utm_source, etc) and is also a security vulnerability.

We need to rebuild the query using validated search paramater data only before storing the url encoded string.

Ideally, we need to set up a searchFacet object that is used to load and validate facets.

## Notes

Merged into [[2396-search-facet-analytics-report-fixes-updates]]