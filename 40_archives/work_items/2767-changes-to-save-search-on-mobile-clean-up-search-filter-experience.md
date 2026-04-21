---
title: 2767-changes-to-save-search-on-mobile-clean-up-search-filter-experience
type: work-item
item_type: task
project: houseplans.net
status: ready
created: 2026-04-21
updated:
due:
url: https://trello.com/c/sXrhbTmd/2767-changes-to-save-search-on-mobile-clean-up-search-filter-experience
---

# 2767-changes-to-save-search-on-mobile-clean-up-search-filter-experience

## Description

Our goal here is 2 things: improve the “save search” experience on mobile by moving it from the edit filters area to the shop page, which will also help drive more account creations, and clean up the search experience on both desktop and mobile by removing spacing and unnecessary elements from the mobile search experience to keep products higher above the fold.

Notes:  
- The “save search” button should only appear once a facet has been interacted with.  
- On mobile, the selected facets should be moved from the floorplans page, to inside the “filters” button at the top above facets. If a user wants to remove a filter, they would click the “filters” button and easily see the option to remove a filter at the top of that area (on top of facets).  
-The current “Save this search” button will be removed from mobile and desktop.

Here is a mock-up of what we want it to look like on mobile:

![](https://trello.com/1/cards/69dd102d31699a4e9baf88d4/attachments/69dffcedc662d8d1cee26431/previews/69dffceec662d8d1cee2648f/download/image.webp "Attachment")

We want the both rows pinned when scrolling on mobile (so pin the results, save search, filters, exterior/floorplans toggle, and the sort)

For desktop, here is the mock up:

![](https://trello.com/1/cards/69dd102d31699a4e9baf88d4/attachments/69dffd3720078a3d80b16725/previews/69dffd3820078a3d80b167ea/download/image.webp "Attachment")

We want these to remain pinned when users scroll down the page on desktop as well.

When you click the new save search button, we want a new modal pop-up that looks like this:

![](https://trello.com/1/cards/69dd102d31699a4e9baf88d4/attachments/69de66fbd9f6af46c1c5c4c2/previews/69de66fbd9f6af46c1c5c507/download/image.webp "Attachment")

If you are not signed in, and you click the red “save search” button, it will pull up the sign in/create account modal. Once the person signs in or creates an account, we want the shop page to pop back up with the new modal pop up that prompts them to create a name for their search.

If you are logged in already, and you click the red save search button, it will just pull up the new modal prompting you to type a name and save your search.

## Notes

