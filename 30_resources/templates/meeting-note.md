<%*
// Step 1: Prompt for meeting title and rename file
const meetingTitle = await tp.system.prompt("Meeting title", "", true);
const dateStr = tp.date.now("YYYY-MM-DD");
await tp.file.rename(`${dateStr} ${meetingTitle}`);

// Step 2: Select area
const area = await tp.system.suggester(
  ["ABHP", "Segment Holdings", "Other"],
  ["abhp", "segment-holdings", "other"],
  true,
  "Select meeting area"
);

// Step 3: Define attendees per area
const attendeeMap = {
  "abhp": ["Shawn K.", "Andre R.", "Craig B.", "Steven R.", "Brian M.", "Taylor S."],
  "segment-holdings": [],
  "other": []
};

const allAttendees = attendeeMap[area] || [];

// Step 4: Select absent attendees (loop until done)
let present = [...allAttendees];
let absent = [];

if (present.length > 0) {
  let selecting = true;
  while (selecting && present.length > 0) {
    const pick = await tp.system.suggester(
      ["Everyone's here", ...present],
      [null, ...present],
      false,
      "Who is absent?"
    );
    if (pick === null) {
      selecting = false;
    } else {
      absent.push(pick);
      present = present.filter(a => a !== pick);
    }
  }
}

// Step 5: Build frontmatter and section content
const presentYaml = present.length > 0
  ? "\n" + present.map(a => `  - ${a}`).join("\n")
  : " []";

const absentYaml = absent.length > 0
  ? "\nabsent:\n" + absent.map(a => `  - ${a}`).join("\n")
  : "";

const sinceLastWeMet = present.length > 0
  ? present.map(a => `### ${a}\n-`).join("\n")
  : "-";

const ratings = present.length > 0
  ? present.map(a => `- ${a}:`).join("\n")
  : "-";

const otherNotes = absent.length > 0
  ? absent.map(a => `- ${a} was not present in this meeting.`).join("\n")
  : "-";
-%>
---
title: "<% meetingTitle %>"
type: meeting
area: <% area %>
created: <% dateStr %>
updated: <% dateStr %>
attendees:<% presentYaml %>
<% absentYaml %>
---

# <% meetingTitle %>

**Date:** <% tp.date.now("MMMM D, YYYY") %>
**Area:** <% area %>

## Intro
---
-
## Metrics
---
-
## Since Last We Met
---
<% sinceLastWeMet %>
## Rock Review
---
-
## Headlines
---
-
## Issues
---
-
## Ratings
---
<% ratings %>

Average:
## Other Notes
---
<% otherNotes %>
