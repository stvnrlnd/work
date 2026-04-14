---
title: State Page Landing Page Parameter for Paid Ads
type: task
task_type: feature
source: abhp
project: abhp
status: ready
created: 2026-04-14
updated: 2026-04-14
due:
trello_id: 2571
---

## Description

If a query parameter called loc_physical_ms is populated, look up the state of the parameter in another table. The csv attached has the data needed for this task.

---

## I) State Based Landing Page Test

Utilize our new State Based pages in our Generic House Plans campaigns to deliver more relevant content (potentially). Essentially, I can create a dynamic parameter that will be added to our landing pages so this url:

[https://www.example.com/house-plans-page](https://www.example.com/house-plans-page)

will become

[https://www.example.com/house-plans-page?location=21137](https://www.example.com/house-plans-page?location=21137)

The location number will correlate to a specific state. So I would need Taylor to create server side redirects that would send users to the State page that correlates to the location ID in the parameter. If I could be a little picky, it would be great for this to be a redirect based on a specific URL and NOT based entirely off of the parameter so I can still test different landing pages as I'll have to add the location parameter to ALL landing pages at a campaign level.

[houseplans.net/state-pages?location=21137](http://houseplans.net/state-pages?location=21137) would go to [houseplans.net/state-pages/california](http://houseplans.net/state-pages/california)

BUT

[http://houseplans.net/floorplans/?location=21137](http://houseplans.net/floorplans/?location=21137) would still go to[http://houseplans.net/floorplans/](http://houseplans.net/floorplans/) (with or without the parameter present)

Here are more specific instructions from Google (well, AI overview). The only part that will really matter to Taylor is Part 4. I can provide the list of all value track parameter location IDs and the states they correlate to.

1. **Configure Location Targeting**


In your single campaign, you must target all desired states.

1. Navigate to the **Locations** menu for your campaign.

2. Add all the states you wish to target in bulk.

3. In **Location options**, select **"People in, or regularly in, your targeted locations"** for the most accurate targeting.

4. **Set the Single Final URL**


All ads in this campaign will share the same Final URL (the base URL of your dynamic page).

- **Final URL:** https://www.example.com/services-page


1. **Implement Tracking Template with ValueTrack Parameter**


You will use a tracking template to append location information to the URL that is sent to your server.

1. In your campaign **Settings**, scroll to **URL options (advanced)**.

2. In the **Tracking template** field, enter:{lpurl}?location={loc_physical_ms}

    - {lpurl} ensures your Final URL is inserted.

    - location={loc_physical_ms} is the crucial part. {loc_physical_ms} is a ValueTrack parameter that Google automatically replaces with the numeric criterion ID of the physical location that triggered the ad.

3. **Configure Your Website's Dynamic Logic**


This is the technical part that your web developer needs to handle. The website must:

- Read the location parameter from the incoming URL (e.g., the URL the user lands on will be https://www.example.com/services-page?location=21137).

- Have a database or mapping that links the Google Location ID (21137 is California's ID) to the appropriate state content or the correct state-specific landing page URL (e.g., https://www.example.com/california-services).

- Dynamically serve the correct content or perform a server-side redirect to the state-specific page.

---

## Notes

