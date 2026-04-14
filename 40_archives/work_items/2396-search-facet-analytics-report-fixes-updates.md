---
title: 2396-search-facet-analytics-report-fixes-updates
type: work-item
item_type: task
project: houseplans.net
status: in-review
created: 2026-04-14
updated:
due: 2026-04-16
url: https://trello.com/c/Im3jpnXK/2396-search-facet-analytics-report-fixes-updates
assignee: Steven R.
---

# 2396-search-facet-analytics-report-fixes-updates

## Description

REVISION:

Change data retention period to 5 years.  
Add ‘click’ data to Facet Combinations report. Ensure at least 100 combinations are visible.  
Make all columns sortable.  
Set default select option to ‘Single Family (remove ‘all’ or only show for devs).  
Change ‘Few’ to 'Limited’ in report title. Set plan threshold to 15 (which is a full page of results).

---

Record a snapshot of a user’s search facets whenever the land on a plan detail page and the referral url is the search page.

Questions we are trying to answer:

- What search facet combinations entered by users do NOT provide very many results?
    
- What search combinations are the most popular?
    
- What search facet combinations have the highest user engagement (plans clicked on)?
    
- What individual facets are the most used across sessions (for re-ordering the search bar)?
    

All of the above are per/category.

We need to store the ‘search results found figure’ with each facet combination.

On the report we need three ranked lists:

- facets selected (by category) - with ‘search results found’
    
- facets engaged with (by category) - with ‘search results found’
    
- single facets by popularity
    

We also need to set up a separate elastic search database with additional space and memory requirements to insulate the product search function.

---

- The report always says 10,000 search sessions - this is a design limitation that needs to be updated
    
- Remove conversion data columns - we don’t want this in this report (average time to convert, conversion rate, converted sessions)
    
- Add “plan type” as an additional filter option in addition to facet type. We would like the ability to only look at multi-family searches, garage searches, etc. with the added layer of facet type on top of that. (EX: Multi-family searches with 3 bedrooms - we want to see what else was searched with those 2 filters)
    
- “Popular Facet Combinations” section
    
    - This section is currently showing us all facets used in a session instead of popular facet combinations. The popular facet combinations are more useful to us vs. seeing all of the different things one person is searching. Ex: we would rather see that 5000 people used modern farmhouse, 3 bed, 2 bath.
        
    - Can we add a column for total # of results as well here? It would be nice to see if there is a particular search facet combo frequently used that we do not have a lot of plans for - great info to share with designers
        
- Add ‘shop' and ‘landing’ page tags to those searches so we can filter them in our reports. Search Page only shows “floorplans” now, but we want it to show us what landing page loaded the facets vs. just the shop page
    

**Future tasks / Still needs to be discussed:**  
- Discuss how to filter out all the partial facet combinations generated as the user is clicking buttons to build out their full query. Just landing on the shop page logs a ‘Single Family’ query  
- Is the Avg. Results necessary? It seems to pull in an average based on anytime that entire facet was used in any search. I don’t know that we need this.

- “Top Facet Usage” section
    
    - On the add/remove ratio, we aren’t currently tracking remove actions - the idea was that the ratio would let us know when a facet is frequently removed. We want to track the remove action, but only if it a single removal happens and not when a user moves to a new category or landing page or hits clear all.
        
        - Perhaps also track ‘clear all’ usage
            

__________________________

Additional Context:

_**What specific questions do you need answered?**_

- Optimizing & re-ordering facets based on usage / what goes at the top can be determined by what is being used the most
    
- To share with Gables for direction on what to design, based on what people are searching for the most
    
- To share with Gables, and potentially other designers if we see that a popular search that does not yield a lot of results
    
- To use popular searches in marketing campaigns
    

Original discussion in card 2314, but re-organized and additional items added in this card.

NEW DOCUMENT STRUCTURE:

```
{
  "user_id": null,
  "session_id": "3j2k8m1dmvej9sokg5mje6mcsk",
  "created_at": "2025-11-17T20:34:39-05:00",
  "single_family" : [
    "facet_list": [],
    "pdp_clicks": [
      {
        "plan_number": "009-00001",
        "url": "",
        "is_landing_page": false,
        "facets_selected": []
      },
      {
        "plan_number": "041-00245",
        "url": "",
        "is_landing_page": false,
        "facets_selected": []
      }
    ]
  ],
  "multi_family" : [
    "facet_list": [],
    "pdp_clicks": [
      {
        "plan_number": "",
        "url": "",
        "facets_selected": []
      }
    ]
  ]
}
```

## Notes

