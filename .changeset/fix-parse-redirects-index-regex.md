---
"@cloudflare/workers-shared": patch
---

Fix `_redirects` infinite-loop detection rejecting paths that only resemble `/index.html`

The check for redirect targets ending in `/index.html` used an unescaped `.`, so any single character matched in its place. Targets such as `/blog/indexXhtml` were wrongly reported as "Infinite loop detected in this rule and has been ignored" and dropped. The dot is now escaped so only a literal `.html` matches.
