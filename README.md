# openclaw-prime-skill

Docs-first priming skill for OpenClaw operators.

Use it before admin work on an OpenClaw setup: gateway changes, channel debugging, remote access, security reviews, deployments, upgrades, model routing, or general operator triage.

## What this repo contains

- `SKILL.md` — the skill definition and workflow
- `references/admin-primer.md` — condensed operator map
- `agents/openai.yaml` — optional prompt surface metadata

## Install

### Codex

Clone the repo:

```bash
git clone https://github.com/NicholasSpisak/openclaw-prime-skill.git ~/Projects/openclaw-prime-skill
```

Link it into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
ln -s ~/Projects/openclaw-prime-skill ~/.codex/skills/openclaw-prime
```

If a previous version exists:

```bash
trash ~/.codex/skills/openclaw-prime
ln -s ~/Projects/openclaw-prime-skill ~/.codex/skills/openclaw-prime
```

Restart the Codex session after linking so the skill list refreshes.

### Other skill-based agent setups

Point your agent at this repo directory, or copy the contents into a skill folder where `SKILL.md` sits at the root.

## Onboarding

### 1. Know the job

This skill is not a generic OpenClaw explainer. It is an operator primer.

Goal:

- refresh the live docs index
- reload the core gateway and architecture pages
- expand only into the task-relevant doc cluster
- separate docs truth from the actual environment
- produce a short operator brief before taking action

### 2. Know the doc flow

The skill starts from live docs, not memory.

Core sources:

- `https://docs.openclaw.ai/llms.txt`
- `https://docs.openclaw.ai/sitemap.xml`
- local primer: [`references/admin-primer.md`](./references/admin-primer.md)

Core pages read every time:

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

### 3. Invoke it

In a Codex session:

```text
Use $openclaw-prime before we touch this gateway config.
```

Typical triggers:

- planning or executing gateway config changes
- debugging pairing, routing, or channel failures
- reviewing auth, proxy, tailscale, or secret handling
- validating deployments, upgrades, or migrations
- answering operator questions where stale docs would be risky

## How to use it effectively

### Best pattern

Ask the agent to use the skill first, then do the real task second.

Examples:

```text
Use $openclaw-prime, then review this remote gateway setup and tell me the auth risks.
```

```text
Use $openclaw-prime, then help me debug Slack channel routing.
```

```text
Use $openclaw-prime, then plan the safest path to migrate this OpenClaw deployment.
```

### What good output looks like

The skill should leave you with three things before deeper work starts:

1. concise OpenClaw architecture + ops summary
2. exact docs pages that govern the next action
3. local facts still needed before any recommendation or change

### What it forces the agent to check

- deployment target
- config source
- auth mode
- exposed surfaces
- active channels and nodes
- secret boundaries
- sandbox and elevated-policy risk

This is the main value: it prevents docs-default assumptions from leaking into a live environment.

## Repo workflow

Pull updates when the OpenClaw docs or the skill workflow changes:

```bash
cd ~/Projects/openclaw-prime-skill
git pull
```

If this repo is symlinked into `~/.codex/skills/openclaw-prime`, no extra install step is needed after updates.

## Source

This skill is built around the live OpenClaw docs at `https://docs.openclaw.ai/`.
