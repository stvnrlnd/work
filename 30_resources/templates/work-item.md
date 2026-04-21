<%*
// Step 1: Select area
const area = await tp.system.suggester(
  ["ABHP", "Segment Holdings", "Personal"],
  ["abhp", "segment-holdings", "personal"],
  true,
  "Who is this work item for?"
);

// Step 2: Prompt for title
const title = await tp.system.prompt("Work item title", "", true);

// Step 3: Rename file
await tp.file.rename(title);

// Step 4: Derive project field
const projectMap = {
  "abhp": "houseplans.net",
  "segment-holdings": "segment-holdings",
  "personal": ""
};
const projectYaml = projectMap[area];

const dateStr = tp.date.now("YYYY-MM-DD");
-%>
---
title: "<% title %>"
type: work-item
item_type: task
project: <% projectYaml %>
status: ready
created: <% dateStr %>
updated:
due:
assignee:
url:
---

# <% title %>

## Description

<!-- Leave blank if no description is available -->

## Notes

