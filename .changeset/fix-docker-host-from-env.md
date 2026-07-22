---
"@cloudflare/containers-shared": patch
---

Fix `getDockerHostFromEnv` ignoring `DOCKER_HOST` and `WRANGLER_DOCKER_HOST`

An operator precedence mistake meant the platform comparison bound tighter than the `??`, so the ternary tested the environment variable itself rather than the platform. Whenever either variable was set the function returned the Windows named pipe path on every platform and never returned the configured value.
