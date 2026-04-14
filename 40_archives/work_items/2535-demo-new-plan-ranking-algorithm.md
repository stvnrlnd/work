---
title: 2535-demo-new-plan-ranking-algorithm
type: work-item
item_type: task
project: houseplans.net
status: in-progress
created: 2026-04-14
updated:
due: 2026-04-01
url: https://trello.com/c/SRYoweo4/2535-demo-new-plan-ranking-algorithm
assignee: Shawn K.
---

# 2535-demo-new-plan-ranking-algorithm

## Description

REVISION 1:

Adjust the algorithm to deduplicate plans as they are inserted, but ensuring that we add 15 organic and then 3 featured on each loop (see proposed scripte below).

Adjust the labels to show the original organic rank and original featured rank (if applicable) on each card. The ‘featured’ tag only needs to show up on a card when it is pulled into the final array from the featured plan list. Otherwise it will not show this tag (but will show the original featured plan rank).

```
<?php

$organic = [/* 25000 product IDs */];
$featured = [/* 500 product IDs */];

function combineSearchResults(array $organic, array $featured, int $organicBatch = 15, int $featuredBatch = 3): array
{
    $result = [];
    $seen = [];

    $organicIndex = 0;
    $featuredIndex = 0;

    $organicChecked = 0;
    $featuredChecked = 0;

    $organicTotal = count($organic);
    $featuredTotal = count($featured);

    while ($organicChecked < $organicTotal || $featuredChecked < $featuredTotal) {

        // Organic batch
        $addedOrganic = 0;

        while (
            $addedOrganic < $organicBatch &&
            $organicChecked < $organicTotal
        ) {
            $product = $organic[$organicIndex++];
            $organicChecked++;

            if (!isset($seen[$product])) {
                $result[] = $product;
                $seen[$product] = true;
                $addedOrganic++;
            }
        }

        // Featured batch
        $addedFeatured = 0;

        while (
            $addedFeatured < $featuredBatch &&
            $featuredChecked < $featuredTotal
        ) {
            $product = $featured[$featuredIndex++];
            $featuredChecked++;

            if (!isset($seen[$product])) {
                $result[] = $product;
                $seen[$product] = true;
                $addedFeatured++;
            }
        }

        // Safety condition if both lists can't add more unique items
        if ($addedOrganic === 0 && $addedFeatured === 0) {
            break;
        }
    }

    return $result;
}

// Example
$searchResults = combineSearchResults($organic, $featured);
```

### This card will need the PHP DS extension installed

E.G. sudo apt install php${VERSION}-ds

![](https://trello.com/1/cards/69431f1cb39c176aa6230e0f/attachments/698a9995325ee2cbdf1a1c5d/download/image.png "Attachment")

![](https://trello.com/1/cards/69431f1cb39c176aa6230e0f/attachments/698b8dd4050cd20a6b32be8d/download/image.png "Attachment")

Using the nightly cron, merge the regular results and featured results lists into one list.

## Notes

