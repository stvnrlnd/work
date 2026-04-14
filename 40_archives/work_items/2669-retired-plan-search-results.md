---
title: 2669-retired-plan-search-results
type: work-item
item_type: task
project: houseplans.net
status: in-review
created: 2026-04-14
updated:
due: 2026-04-28
url: https://trello.com/c/20wGGi4C/2669-retired-plan-search-results
assignee: Steven R.
---

# 2669-retired-plan-search-results

## Description

The url used to show a user similar plans when they navigate to a retired plan page is missing the array index for some search facets.

Look at the bedroom and garage facets below:

[https://www.houseplans.net/floorplans/?category_id=1&sqft_min=1146&sqft_max=1646&bedrooms=2&levels=1&garages=2&redirect=true](https://www.houseplans.net/floorplans/?category_id=1&sqft_min=1146&sqft_max=1646&bedrooms=2&levels=1&garages=2&redirect=true)

should be:

[https://www.houseplans.net/floorplans/?category_id=1&sqft_min=1146&sqft_max=1646&**bedrooms[2]**=2&levels=1&**garages[2]**=2&redirect=true](https://www.houseplans.net/floorplans/?category_id=1&sqft_min=1146&sqft_max=1646&bedrooms%5B2%5D=2&levels=1&garages%5B2%5D=2&redirect=true)

## Notes

