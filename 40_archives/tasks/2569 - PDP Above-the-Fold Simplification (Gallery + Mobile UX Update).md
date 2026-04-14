---
title: PDP Above-the-Fold Simplification (Gallery + Mobile UX Update)
type: task
task_type: feature
source: abhp
project: abhp
status: ready
created: 2026-04-14
updated: 2026-04-14
due:
trello_id: 2569
---

## Description

## REQUEST SUMMARY

Update the above-the-fold layout for all Floor Plan PDPs to improve usability, reduce clutter, and prioritize the new gallery experience while reusing existing components.

- Current PDP above-the-fold contains too many competing elements (icons, tabs, quick specs).

- Gallery does not feel like the primary decision driver, especially on mobile.

- Mobile experience is vertically crowded and visually noisy.


## DETAILED SPECIFICATIONS

### Launch New Gallery Priority

- Make the Gallery the dominant above-the-fold element by adding the #of photos icon.

- Integrate the new gallery:

    - Main image carousel

    - REMOVE Arrows

    - Add Photo count badge

    - Video + 360 buttons stay where they are.

- Ensure gallery renders first


### 2. Action Icons (Favorite / Rule Out / Note / Share)

- Swap the location of Note and Share to pull the share icon to the right side.

- Keep all existing functionality but move them a bit closer together, reduce the size of the icons, and remove the text below.

- Ensure icons do not compete with the gallery

- On mobile:

    - Reduce vertical space used

    - Icons should not push the gallery below the fold and should be reduced in size.


### 3. Tabs (Floor Plans / Exterior / Interior / Build Photos)

- Keep tabs (no removal)

    - Remove the dropdown for Build photos,

        - Keep "Build Photos" And "Builds" on mobile. Like this:
            [Screenshot 2026-01-07 at 10.37.44 AM.png](https://trello.com/1/cards/69612209a4e5d210fdd1f104/attachments/6961487ffd71ba6939f184e5/download/Screenshot_2026-01-07_at_10.37.44_AM.png)

- Reduce visual prominence

- Position directly under the gallery

- Treat as secondary navigation, and upon engaging launch the new gallery and take the user to which ever cta they had selected.


### 4. Quick Specs Row (Key Change)

Desktop

- Keep all current quick specs, including:

    - SQ FT

    - Beds

    - Baths

    - 1/2 Baths

    - Garage

    - Stories

    - Width

    - Depth


Mobile

- Remove Width and Depth from the visible quick-spec icon row only

- Keep:

    - SQ FT

    - Beds

    - Baths

    - 1/2 Baths

    - Garage

    - Stories

- Width and Depth:

    - Must remain in the mobile DOM

    - Can appear lower on the page or in another specs section

    - Should be hidden via responsive CSS (not removed server-side)


[Screenshot 2026-01-06 at 4.35.00 PM.png](https://trello.com/1/cards/69612209a4e5d210fdd1f104/attachments/69612219912b0125f9f476a8/download/Screenshot_2026-01-06_at_4.35.00_PM.png)

### 5. Purchase Panel (Right Rail)

- No functional changes

- Keep:

    - Package selection

    - Foundation selection

    - Add to Cart

- Ensure right rail does not force gallery below fold on smaller screens


### 6. Cost-to-Build Module

- Keep module but alter it to be smaller. and change the CTA:

- Visually de-emphasize relative to Add to Cart

- Should not appear above gallery or core plan info on mobile


## MOBILE-SPECIFIC SUMMARY

- Gallery is the primary visual element

- Reduced icon and spec clutter

- Width/Depth hidden from quick specs but still accessible

- No SEO risk (responsive-only visibility change.


Taylor and I spoke 1-9-26 and discuss various ways to trim pixels to make this work for desktop. Please discuss with him or I if you have questions or concerns. AND no I do not want Double Cost to build Icons, that was a joke. Please do not add both. It can be removed.

## Notes

