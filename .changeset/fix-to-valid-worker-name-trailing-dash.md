---
"@cloudflare/workers-utils": patch
---

Fix `toValidWorkerName` producing a name that ends in a dash

Leading and trailing dashes were stripped before the name was truncated to the 63 character limit, so a name cut immediately after an internal dash ended in `-` — which is rejected as invalid. Dashes are now stripped again after truncating.
