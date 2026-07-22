---
"@cloudflare/workers-utils": patch
---

Fix `parseHumanDuration` returning 7x too large a value for months and years

The `month` and `year` units (and their `mo`, `yr` and `y` aliases) were derived from the number of seconds in a week rather than in a day, so `1month` parsed as 210 days and `1year` as roughly 7 years. They are now 30 and 365 days respectively.
