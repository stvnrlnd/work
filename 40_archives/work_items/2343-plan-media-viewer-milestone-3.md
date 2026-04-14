---
title: 2343-plan-media-viewer-milestone-3
type: work-item
item_type: task
project: houseplans.net
status: done
created: 2026-04-14
updated:
due: 2026-02-13
url: https://trello.com/c/5Wub1Re0/2343-plan-media-viewer-milestone-3
assignee: Andre R.
---

# 2343-plan-media-viewer-milestone-3

## Description

Revision 4:

Refactor modal from iframe to ajax/htmx, etc.

Pinch-zoom catches, possibly due to hover effects.

Double check 360 fullscreen feature after refactor is complete.

---

Revisions 3:

Move media viewer link JS to head so it is caught earlier. I frequently click the thumbnail and the image opens in a new tab instead of opening the media viewer.

Add fullscreenToggle button to 360 tour

Resolve z-index issue with nav arrows when loading the media viewer through the floor plan images slider.

![](https://trello.com/1/cards/68c96fadb6db93e648e7f565/attachments/69335e5ce002edb3c0bc38a3/download/image.png "Attachment")

---

Revisions 2:  
[https://docs.google.com/document/d/17ZeWm6DPjnGtESaAAsAKN3oUzyNn1QttOd2VNAtTpeU/edit?tab=t.0](https://docs.google.com/document/d/17ZeWm6DPjnGtESaAAsAKN3oUzyNn1QttOd2VNAtTpeU/edit?tab=t.0)

---

Revisions 1:

Better definition for tabs.

Make sub-navigation items appear as bubbles, and include horizontal scrolling when necessary.

Put all build albums in a single tab, and provide a select box in the sub-navigation area for selecting which one to view.

Adjust tab order, and shorten tab titles when needed to fit into viewport.

Hide ‘See it on land’ tab (should be last when activated).

Change reverse icon to match pdp icon (possibly change to match AHP so it fits with label better).

Reset scroll to the top every time a tab is switched to.

Add Primary Style + Category label to match plan detail page title

Add Beds, Baths, Sq Ft to header in a single row (try with and without small icons).

Adjust image container so there isn’t any space between the image and the caption.

Make the caption font a little larger, and make the caption container background slightly darker.

Add vertical space between floorplan images.

Remove image type headings (interior, exterior, Built in Georgia, etc).

Add 5px rounded corners to images.

---

Make it a modal that loads on the plan detail page, and add a close button or back button. The modal should open with animation, and should be full width size on smaller devices, but have a max-size and some margins on desktop. The modal content should not load unless it is opened.

---

## Notes

