---
title: 2569-pdp-above-the-fold-simplification-gallery-mobile-ux-update
type: work-item
item_type: task
project: houseplans.net
status: done
created: 2026-04-14
updated:
due: 2026-04-10
url: https://trello.com/c/U5eAqVpH/2569-pdp-above-the-fold-simplification-gallery-mobile-ux-update
assignee: Andre R.
---

# 2569-pdp-above-the-fold-simplification-gallery-mobile-ux-update

## Description

REVISION 3:  
The exclusive ribbon is not lined correct on mobile for plan detail page.  
Line is missing between 1/2 bath and car icons.  Also in image  
Reverse button should have icon on both plan detail page and modal.  Modal should also have reverse and undo spelled out.

REVISION 2:  
The modal close button does not stop the youtube video if it is playing.

Add a Reverse button below the main page image (like production) along with the cart related note. In the modal, once reverse button is engaged it should show as undo opposed to “reversed” to match the reverse buttons on the main page.

Once you are in the modal and select an image, once you interact with the arrows (when tapping just below the arrow) it will zoom in (but should not). Video attached.

---

REVISION 1:

Keep these changes (and discard the rest):  
- H1 Title  
- Main Image and Icons  
- Low Price Guarantee

‘See Details’ in the Low Price Guarantee should be kept together

Add a blue border to the original ‘More Plans By This Designer’ button

The new Floorplans/Exterior/Interior/Builds buttons should match the 360/video/photos buttons in style (pill shaped, blue text and border, white background).

---

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
        
        - Keep “Build Photos” And “Builds” on mobile. Like this:  
            [Screenshot 2026-01-07 at 10.37.44 AM.png](https://trello.com/1/cards/69612209a4e5d210fdd1f104/attachments/6961487ffd71ba6939f184e5/download/Screenshot_2026-01-07_at_10.37.44_AM.png)
            
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
        

[Screenshot 2026-01-06 at 4.35.00 PM.png](https://trello.com/1/cards/69612209a4e5d210fdd1f104/attachments/69612219912b0125f9f476a8/download/Screenshot_2026-01-06_at_4.35.00_PM.png)

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

---

Updates from [https://trello.com/c/5Wub1Re0/2343-plan-media-viewer-milestone-3](https://trello.com/c/5Wub1Re0/2343-plan-media-viewer-milestone-3) :  
Make the native fullscreen functionality work correctly. We do not need to preserve the close/back button customization, as we will not be sending users to the tour urls directly anymore (i.e. we will only be loading them in the media viewer through an iframe). This may require changing our existing tours and the tour creation app.

While reviewing this today and the above the fold page, we wanted to update the reveres how it currently opperates on Dev 1.

**Reverse on the gallery:**

1. Use our current Reverse icon in the gallery: [Reverse button added.png](https://trello.com/1/cards/68c96fadb6db93e648e7f565/attachments/6973ebaa358240dfccee959b/download/Reverse_button_added.png)
    
2. Upon engagement, make sure the Important notice is displayed and our current Undo cta is displayed to show it has been engaged. [Gallery Reverse engaged.png](https://trello.com/1/cards/68c96fadb6db93e648e7f565/attachments/6973ebac7fb70c721d36fed5/download/Gallery_Reverse_engaged.png)
    

**Single image in gallery:**

1. Upon clicking on the image, we need to show the reverse icon and cta in white to contrast the black background: [reverse button added to single image.png](https://trello.com/1/cards/68c96fadb6db93e648e7f565/attachments/6973ec7402db89f14aad62dd/download/reverse_button_added_to_single_image.png)
    
2. Upon engagement, add the note below the image and make sure the Undo reverse button is engaged: [Single image reverse engaged.png](https://trello.com/1/cards/68c96fadb6db93e648e7f565/attachments/6973ec75c18acd0fca4efc6e/download/Single_image_reverse_engaged.png)

## Notes

