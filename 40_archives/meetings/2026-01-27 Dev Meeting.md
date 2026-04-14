## Intro
---
Are you anti- or pro-Godzilla?
## Metrics
---
-
## Since Last We Met
---
### Shawn K.
- [[2572 - BUG - Promotion Level not showing]]
- [[2377 - AI Tool for Detecting Features]]
### Andre R.
- [[2343 - Plan Media Viewer - Milestone 3]]
- [[2569 - PDP Above-the-Fold Simplification (Gallery + Mobile UX Update)]]
	- Working on above tasks together since related
### Craig B.
- [[2441 - Set Up WebPageTest Automation]]
	- Continuing with automated tests for search filters, moving to checkout
### Steven R.
- [[2526 - Customer Receipt Delivery Delay Notices]] Moved to Review
- [[2571 - State Page Landing Page Parameter for Paid Ads]]
	- Plan to finish up today
- [[2449 - Mod quote request save feature]] On Hold
	- Taylor S. sent private slack message -- pushes LocalStorage, does not answers technical questions, uses AI code and Fathom recap in vaguely threatening way. See [[abhp/notes/2025-12-16|2025-12-16]] meeting notes, ref video.
	- Taylor: Put current work on ice and may circle back later, use AI code and may need to tweak
### Brian M.
- [[2075 - CSS Framework]] 
- [[2359 - Bulk Image Uploader Engineering Plan]] 
	- Will finish today, then make new card
- [[2455 - BUG - Similar Plans Slider]] In Review
- [[2466 - Update Tier Image on Pro Services Page]] In Review
- [[2497 - Download email subject line and dashboard link]] In Review
- [[2129  - Group Order History Events]] In Review
- [[1947 - Add plan tags for Interior Photos & Build Photos]] In Review
- [[2205 - Add Notes section in the back end for Build Photo Albums]] In Review
- [[2381 - Purchased without mods report adjustment]] In Review
- [[2561 - Designer Deliverable Download File Name]] In Review
- [[2555 - BUG - Wordpress Lazy Loading]] In Review
### Taylor S.
- [[2578 - Add Front Tag for Georgia orders]] 
- [[2299 - Research - Send Users Text Updates for Quotes & Order Statuses]]
- [[2567 - Document Incident Report Scripts]] In Review
- [[2441 - Set Up WebPageTest Automation]] In Review
- [[2543 - Upgrade to PHP 8.5]] In Review
- [[2532 - Add Composer update to PHP install script]] In Review
- [[2488 - Discount Scenarios]] In Review
## Rock Review
---
- [[2075 - CSS Framework]] Brian M.
## Headlines
---
-
## Issues
---
- [[2396 - Search Facet Analytics Report Fixes & Updates]]
	- revision points, on hold
	- will have Shawn spin up new elastic db for this data, probably add index limts
- [[2574 - Sanitize Query Parameters for Save This Search]]
	- Related to above
	- right now just sanitizing url string, but not being sanitized, can use snitized url for search facet analytics report
	- Tag Steven
- [[2582 - Elastic Server for Analytics]]
	- Tag shawn
- [[2556 - Add intro Content to State Page]]
	- couple of hardcoded paragraphs
- [[2535 - DEMO - New Plan Ranking Algorithm]]
	- Taylor wants to work on with Shawn
	- Taking featured plans and reg plans, merging
- [[2570 - Require Pro Customers to sign in during checkout]]
	- right now when matching email is found, login popup shows, but can dismiss
	- do not allow pro users to continue without logging in
	- not a lot of thought about what should say or when should happen
	- May try to use different email
	- !! security concern: exposing that account exists (Steven thinks, Taylor verbalizes -- Taylor finds it annoying when sites don't tell you if email/username was found and password was wrong)
	- pro users may never checkout as guest, all other users can checkout as guest
	- Taylor: "something weird that's niggling at the back of my mind about trapping customers in auth modal"
	- Brian: "maybe we can create a new frontend for pro users, same backend"
- [[2549 - Rich Snippets review card FAQ and Product]]
	- on product and search page, just need to review for google standards
	- goal is to get featured on google
-  [[200 - Order Revisions Before Releasing to Designer]]
	- restart, a lot has changed about order process and a lot more changes are coming
	- should be rewritten as a minimal update that allows some db_operations functionality
- [[2521 - Accessibility Audit]]
	- Do accessibility audit, come up with 2-6point tasks that get most bang for buck
	- Probably a lot of AI fixes
	- Maybe a Craig task? Was moved to Craig
## Ratings
---
- Shawn K.:
- Andre R.:
- Craig B.:
- Brian M.:
- Taylor S.:
- Steven R.:

Average:
## Other Notes
---
- Shawn passing on today's meeting, sore throat
- AI notetaker does not keep personal conversation
- What's for lunch:
	- Taylor: ham and mustard (no bread)
	- Brian: fried rice (no mustard)
	- Steven: No lunch yet
	- Craig: making lunch, beef & fat-free cheese and spinach wrap
	- Andre: Tomato and orzo sausage soup (with mustard)
- Taylor S. van damaged by storm/limb
- Craig B. icy weather
- Brian M. snowy weather
- When you have a new card with new number and want to work from old work, make a note in the new card and make new branch from old branch with new card number -- Taylor/Brian filter by card number for branch