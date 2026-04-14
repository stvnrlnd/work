---
title: 2449-mod-quote-request-save-feature
type: work-item
item_type: task
project: houseplans.net
status: done
created: 2026-04-14
updated:
due: 2026-03-02
url: https://trello.com/c/f8iqhzL0/2449-mod-quote-request-save-feature
assignee: Steven R.
---

# 2449-mod-quote-request-save-feature

## Description

REVISED SCOPE:

We want to use local storage for the Save Mod Quote task so it will auto-save (like google docs) and not require any manual input from the user. We get a lot of reports of customers losing their data by mistake, and the manual save process doesn't mitigate that as well as auto-save.  
I generated a script to auto-save and restore the form data using local storage (see attached) and it does almost everything we need right out of the box. Just paste the script at the bottom of the form to see it in action.

The only thing it doesn't handle properly is any additional description fields added by the user. In addition, the restore function needs to fire a simple dialog asking the user if they want to restore their saved draft (or discard it), and we need a 'Clear this form' button or 'reset' link at the bottom of the form (especially for employees).

---

**PRIMARY USER**

Customer

---

**REQUEST SUMMARY**

Ability to save a quote request to a customers account

---

**ADDITIONAL CONTEXT / PROBLEM DESCRIPTION**

Some customer need more time to put together their full request, sometimes to have somebody else look it over. Next to the send button, possibly put a “Save for later” button, if they aren’t logged into their account or don't have one, clicking save for later would require a login or to sign up for an account.

Currently, all info is lost if not submitted immediately.

---

**DETAILED SPECIFICATIONS**

---

**UX WIREFRAME / IMAGES:**

## Notes

