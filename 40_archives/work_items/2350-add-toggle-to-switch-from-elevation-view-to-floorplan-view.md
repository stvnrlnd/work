---
title: 2350-add-toggle-to-switch-from-elevation-view-to-floorplan-view
type: work-item
item_type: task
project: houseplans.net
status: in-review
created: 2026-04-14
updated:
due: 2026-04-17
url: https://trello.com/c/dcDNihZe/2350-add-toggle-to-switch-from-elevation-view-to-floorplan-view
assignee: Steven R.
---

# 2350-add-toggle-to-switch-from-elevation-view-to-floorplan-view

## Description

REVISION 1:

- Change the “Elevation” label on the toggle to “Exterior”, and change all “blueprint” references to “floor plan”. Even though the term “blueprint” is still used colloquially, it is not technically correct and has fallen out of use within the industry.
    
- The requirement for adding the toggle to the user Favorites page was overlooked. The display mode for this page should be set independently of the shop page.
    
- When reloading the shop page (especially coming back to it from elsewhere) the toggle display is delayed when in “floor plan” mode due to the local-storage lookup.
    

One way to fix the toggle display lag (and simplify things at the same time) would be to store the display mode setting in a cookie, and then set a single css class on the body tag to identify the page’s mode. Switching modes would only require a single class toggle, and a cookie would allow us to set it on the server (no JS delay). A cookie would also provide automatic visibility for the setting, in case we ever wanted to monitor usage or save it to the user profile.

---

We’d like to have a toggle to switch to floorplan view on the search level, as well as within the favorites section of an account.

_________________________

Context: Screenshots of how our competitors do it in the comments

We want it to show just to the left of the sort select box (or just above on mobile). This applies to the search page and the user favorites page.

![](https://trello.com/1/cards/68cc17e01e09f3345c9e3522/attachments/690a212cb8bada3e2b9891f6/download/image.png "Attachment")

![](https://trello.com/1/cards/68cc17e01e09f3345c9e3522/attachments/690a21fa2f6aa0fc01780d32/download/image.png "Attachment")

## Notes

