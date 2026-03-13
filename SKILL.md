---
name: "openclaw-prime"
description: "Prime a context window with OpenClaw infrastructure, gateway, channel, security, and operator knowledge from the OpenClaw docs. Use before answering admin questions, planning or executing configuration changes, debugging gateways or channels, reviewing deployments, or making operational decisions on an OpenClaw setup."
---

# OpenClaw Prime

## Overview

Load the OpenClaw docs into working memory before doing operator work. Use this skill to build a current mental model of the gateway, config, security model, channels, nodes, and deployment surfaces, then carry that context into the actual admin task.

## Prime Workflow

### 1. Refresh the docs index

Start from the live docs, not memory.

- Read `https://docs.openclaw.ai/llms.txt` to get the current page list.
- If recency matters, check `https://docs.openclaw.ai/sitemap.xml` for recently changed pages.
- Read [admin-primer.md](./references/admin-primer.md) for the distilled operator map before diving into page-specific docs.

### 2. Read the core pages every time

Read these pages for almost any infra or admin task:

- `https://docs.openclaw.ai/index.md`
- `https://docs.openclaw.ai/start/hubs.md`
- `https://docs.openclaw.ai/gateway/index.md`
- `https://docs.openclaw.ai/gateway/configuration.md`
- `https://docs.openclaw.ai/gateway/configuration-reference.md`
- `https://docs.openclaw.ai/gateway/security/index.md`
- `https://docs.openclaw.ai/gateway/remote.md`
- `https://docs.openclaw.ai/gateway/troubleshooting.md`
- `https://docs.openclaw.ai/cli/index.md`
- `https://docs.openclaw.ai/channels/index.md`
- `https://docs.openclaw.ai/concepts/architecture.md`
- `https://docs.openclaw.ai/concepts/multi-agent.md`

### 3. Expand by task

Pick the smallest relevant doc set for the task.

- Gateway auth or networking:
  `gateway/authentication.md`, `gateway/tailscale.md`, `gateway/trusted-proxy-auth.md`, `gateway/network-model.md`
- Config or secrets:
  `gateway/secrets.md`, `gateway/configuration-examples.md`, `auth-credential-semantics.md`
- Health or debugging:
  `gateway/doctor.md`, `gateway/health.md`, `gateway/logging.md`, `help/troubleshooting.md`
- Channels or pairing:
  `channels/channel-routing.md`, `channels/pairing.md`, `channels/troubleshooting.md`, plus the specific channel page
- Nodes or device surfaces:
  `nodes/index.md`, the relevant node page, and platform docs
- Deployment or upgrades:
  `install/index.md`, the relevant install target page, `install/updating.md`, `install/migrating.md`
- Model behavior:
  `concepts/model-providers.md`, `concepts/model-failover.md`, `concepts/models.md`
- Automations:
  `automation/*.md` pages relevant to the hook, cron, poll, or webhook workflow

### 4. Separate docs truth from local truth

After priming from docs, inspect the actual environment before recommending or executing changes.

- Identify deployment target: local, VM, Docker, cloud, macOS bundle, or remote gateway.
- Identify config source: `~/.openclaw/openclaw.json`, env overrides, secret storage, reverse proxy, tailnet, service manager.
- Identify active surfaces: channels, nodes, models, auth mode, exposed ports, paired devices.
- Identify risk boundaries: bearer tokens, trusted proxies, allowlists, sandbox and elevated policy.

Do not assume the local setup matches the docs defaults.

### 5. Produce a short operator brief

Before acting, summarize:

- What OpenClaw component is involved
- What config or secret surface matters
- What docs pages govern the change
- What operational risks exist
- What is still unknown from the live environment

Keep it short. Enough to unblock the real admin task.

## Output Standard

When this skill is invoked, leave the user with:

1. A concise OpenClaw architecture and ops summary
2. The exact docs pages that matter for the next action
3. The local-environment facts still needed before making changes

If a task depends on changing docs-sensitive behavior, re-open the live page immediately before giving final guidance.
