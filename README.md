# VK LED Uptime Guardian

Independent, no-cost recovery controller for the private VK LED Business OS.

It contains no application source code or business data. A scheduled GitHub
Actions workflow checks production readiness and, only after repeated failures,
uses a repository-scoped SSH deploy key to create a recovery commit in the
private source repository. Hostinger's existing Git integration then performs a
clean production deployment.

## Safety controls

- Read-only permissions in this public repository.
- No pull-request trigger, so secrets are never used for forked code.
- A 20-minute cooldown prevents deployment loops.
- Recovery is accepted only after database, schema and deployed revision checks.
- The SSH key can write only to the VK LED Business OS repository.
