---
title: 2310-user-marketing-attribution-history
type: work-item
item_type: task
project: houseplans.net
status: in-review
created: 2026-04-14
updated:
due: 2026-04-22
url: https://trello.com/c/FxlWhZDR/2310-user-marketing-attribution-history
assignee: Steven R.
---

# 2310-user-marketing-attribution-history

## Description

REIVISON 2:

Please disable the robots check in the VisitorTrackingService class so we can see all activity (human and bot). It could be super useful to filter this traffic out at some point, but I’d like to see everything for now.

There are also some extra code changes that I’d like removed:  
- GuardFormSubmission changes  
- Composer classmap loading (along with associated use statements)  
- The global session_start function added to config  
- The server identity/load balancing code added to config

Thanks!

---

REVISION 1:

Create a clients table for storing an anonymous client_id. The table should have a datetime for when it was set, along with the client’s IP and User-Agent.

Generate an abhp-client cookie with this id (if it is not already set), and set it to never expire.

Create a user_authentications table that logs every user sign in, storing the user_id, the datetime, the user’s IP, and the associated client_id.

Create a client_marketing_attribution table that stores marketing attribution strings, the datetime they were recorded, and the client_id.

**If a user is logged in as an admin, bypass all of the above.**

NOTE: We do not need to remove the marketing attribution fields on the users table at this time, and should continue to collect and store this information as it is currently being done. These fields represent a unique snapshot of marketing history at the time the user account is created, and the marketing team needs consistency for this data. The new tables will of course include this information as well, but we want to wait until we have 3-6 months of data collected with the new approach before we make changes to existing reports and the user table export.

---

Instead of storing marketing history on the user profile, let’s create a secondary table that is User ID, utm source, click ID, and date, and then keep a log of every marketing interaction and date attributed to a user. This would give us a time series history for every user of every different marketing interaction they’ve had with us.

CONTEXT: If needed, it was discussed on this fathom 5:20-6:30: [https://fathom.video/share/-X3RSmZpWyYs6dmz-bFw71sWtMG7HCnS?tab=summary&timestamp=316.0&utm_campaign=postmeetingsummary&utm_content=summary_item&utm_medium=email](https://fathom.video/share/-X3RSmZpWyYs6dmz-bFw71sWtMG7HCnS?tab=summary&timestamp=316.0&utm_campaign=postmeetingsummary&utm_content=summary_item&utm_medium=email)
## Notes

