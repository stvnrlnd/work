---
title: 2663-images-missing-alt-attributes
type: work-item
item_type: task
project: houseplans.net
status: in-review
created: 2026-04-14
updated:
due: 2026-04-14
url: https://trello.com/c/hwACt6EF/2663-images-missing-alt-attributes
assignee: Steven R.
---

# 2663-images-missing-alt-attributes

## Description

**Problem:**  
Images without alt text are not described to screen reader users, causing loss of meaningful information when images convey content or function.  
**Solution:**  
Provide meaningful alt text for informative images. Use empty alt="" for decorative images.

- **Homepage →**
    
    - Featured-style-card>img  
        (Featured Styles/Featured Collections images; multiple instances)
        
    - Img  
        (Same as alt attributes)
        
    - Img.check-circl-icon
        
    - img.info-icon
        
- **Search Page →**
    
    - Img  
        (Generic image elements within search banner and results)
        
    - Img.check-circle-icon
        
    - img.info-icon
        
    - img.mobile-navigator-icon
        
- **Plan Detail →**
    
    - img  
        (Multiple plan detail images flagged without alt text)
        
    - img.plan-card-info-icon  
        (Informational icons used within plan details; repeated component)
        
    - img.mobile-navigator-icon  
        (Icons used in interactive contexts on the plan details page)
        
- **Cart →**
    
    - Imag.mobile-navigator-icon  
        (Favorites icon, flagged for alt text redundancy)
        
- **Checkout →**
    
    - Imag.mobile-navigator-icon  
        (Favorites icon, flagged for alt text redundancy)
        
- **Dashboard →**
    
    - img  
        (Generic image elements flagged without alt attributes)
        
    - img.mobile-navigator-icon  
        (Account / navigation icon flagged)
        
- **Contact Us →**
    
    - mg.mobile-navigator-icon  
        (Account / navigation icon flagged)

## Notes

