# OpenClaw Admin Primer

Use this file as the first-pass mental model, then refresh the live docs from `https://docs.openclaw.ai/llms.txt`.

## What OpenClaw is

OpenClaw is a multi-channel gateway for AI agents that runs across local and remote surfaces. The docs position the gateway as the core operator surface, with channels, nodes, models, sessions, and security layered around it.

## Operator-first docs map

Read these first for most admin work:

- `index.md`
- `start/hubs.md`
- `gateway/index.md`
- `gateway/configuration.md`
- `gateway/configuration-reference.md`
- `gateway/security/index.md`
- `gateway/remote.md`
- `gateway/troubleshooting.md`
- `cli/index.md`
- `channels/index.md`
- `concepts/architecture.md`
- `concepts/multi-agent.md`

## Core concepts to keep in memory

### Gateway

- The gateway is the central control plane.
- The docs emphasize configuration, health, logs, locking, remote access, pairing, secrets, sandboxing, and troubleshooting as recurring operator concerns.
- `gateway/configuration-reference.md` is the field-level source of truth for `~/.openclaw/openclaw.json`.

### Security and auth

- Default posture is local-first and token-protected.
- Remote access docs emphasize SSH tunnels and Tailscale.
- Trusted proxy auth exists, but the docs frame it as a deliberate reverse-proxy pattern, not a casual default.
- Sandbox policy, tool policy, and elevated permissions are separate control surfaces and should not be collapsed together.

### Channels

- OpenClaw supports a large set of messaging and collaboration channels.
- Channel work usually needs three docs buckets:
  the generic channels overview, channel routing and pairing docs, and the specific channel page.
- Troubleshooting has both generic channel troubleshooting and channel-specific setup pages.

### Nodes and platforms

- Nodes cover device capabilities like audio, camera, images, talk mode, voice wake, and media understanding.
- Platform docs matter when the task crosses into iOS, Android, Linux, macOS, or cloud deployment specifics.

### Models and routing

- Model provider, failover, and multi-agent docs are core to runtime behavior.
- Session and context docs matter when behavior looks like routing, memory, or compaction rather than infrastructure failure.

## High-value doc clusters by task

### Configure or reconfigure a gateway

- `gateway/configuration.md`
- `gateway/configuration-reference.md`
- `gateway/configuration-examples.md`
- `gateway/secrets.md`
- `gateway/security/index.md`

### Expose or access a remote gateway

- `gateway/remote.md`
- `gateway/remote-gateway-readme.md`
- `gateway/tailscale.md`
- `gateway/trusted-proxy-auth.md`
- `gateway/network-model.md`

### Diagnose a broken setup

- `gateway/doctor.md`
- `gateway/health.md`
- `gateway/logging.md`
- `gateway/troubleshooting.md`
- `help/troubleshooting.md`

### Pair or debug channels

- `channels/index.md`
- `channels/channel-routing.md`
- `channels/pairing.md`
- `channels/troubleshooting.md`
- the specific channel page under `channels/`

### Upgrade, migrate, or deploy

- `install/index.md`
- the target deployment page under `install/`
- `install/updating.md`
- `install/migrating.md`

### Reason about architecture or agent behavior

- `concepts/architecture.md`
- `concepts/agent.md`
- `concepts/agent-loop.md`
- `concepts/multi-agent.md`
- `concepts/session.md`
- `concepts/model-providers.md`
- `concepts/model-failover.md`

## Current live-doc signals

These pages were recently updated in the live sitemap during skill creation and are worth re-checking when relevant:

- `channels/slack`
- `channels/telegram`
- `channels/troubleshooting`
- `channels/msteams`
- `channels/pairing`
- `channels/channel-routing`

Treat channel behavior as especially time-sensitive.

## Working rules for future runs

- Use live docs first; this file is only a primer.
- Re-open the exact page that governs the action before giving admin advice.
- Separate docs assumptions from observed local state.
- Identify the deployment target and auth model before changing anything.
- If the task is risky, summarize config surfaces, secrets, auth, ports, and rollback path before execution.
