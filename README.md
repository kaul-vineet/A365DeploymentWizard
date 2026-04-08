# CAPE Tutorial: Deploy A365 Agent

> Your personal guide through the full Microsoft Agent 365 deployment — from
> prerequisites to a live agent in Teams, with Defender observability and
> Copilot Studio MCP integration.

## Why Use This Skill

Deploying a Microsoft Agent 365 agent involves dozens of CLI commands, browser sign-ins, permission grants, and portal configurations spread across Azure, Entra ID, Teams, and Defender — each with its own pitfalls. This skill turns that gauntlet into a guided conversation. It executes every command for you, explains *why* each step matters, validates results before moving on, and remembers where you left off if you need to step away. Whether you're a first-timer or deploying your fifth agent, the Road gets you from zero to a live, tested agent in Teams — without missing a stone.

## What It Does

This skill walks you through deploying a Microsoft Agent 365 sample app
**step by step**, as an interactive tutorial. It doesn't just tell you what
to run — it explains *why* each step matters, executes commands for you,
validates results, and handles errors along the way.

```
§0 · Clone the sample repository
§1 · CLI Deployment — config init → setup all → publish → deploy
§2 · Admin Centre activation → Teams setup → MCP tool extension
§3 · Defender — advanced hunting queries & detection rules
§4 · Copilot Studio — no-code agent with MCP servers
```

## How to Use

### Start a new deployment

Select the agent and say:

```
start
```

Or use any trigger phrase:
- `deploy a365 agent`
- `a365 deployment guide`
- `deploy sample agent app`

### Resume a previous session

```
resume
```

The skill remembers where you left off — including all your parameters.

### Navigate

At any step you can say:

| Command | What it does |
|---------|-------------|
| `continue` | Advance to the next step |
| `exit` | Save progress and return to Copilot CLI |
| `status` | Show current position on the Road |
| `skip` | Skip the current step |
| `go to §2` | Jump to a specific section |
| `go to step 25` | Jump to a specific step |
| `back` | Go back one step |

### Exit and return later

Say `exit` at any step. Your progress and all collected parameters are
saved. When you come back, select the agent and say `resume`.

## Prerequisites

Before starting, ensure you have:

- [ ] Frontier Preview Programme enrolment
- [ ] Global Administrator role in Entra ID
- [ ] Microsoft Agent 365 Frontier licence
- [ ] .NET 8.0 SDK, A365 CLI, Git, VS Code, Python 3.10+
- [ ] Azure subscription with Owner/Contributor role
- [ ] Client app registered in Entra ID (5 delegated permissions)
- [ ] AI model deployed in Azure AI Foundry

The skill will confirm each of these before you begin.

## What the Skill Executes

The skill runs commands directly — you don't need to copy-paste anything.

| Command Type | Executed by |
|-------------|-------------|
| Verification (`az account show`, Graph API checks) | Skill runs automatically |
| Non-interactive (`git clone`, `a365 deploy`, `code .`) | Skill runs automatically |
| Interactive with browser auth (`a365 config init`, `setup all`, `publish`) | Skill runs, you sign in when browser opens |
| UI steps (Admin Centre, Teams, Copilot Studio) | Skill guides you step by step |

## Installation

This skill is a user-level custom agent. The file is located at:

```
~/.copilot/agents/deploy-a365.md
```

No additional installation needed. After placing the file, restart
Copilot CLI (`/restart`) and select it via `/agent`.

## Source

Built from the official workshop guides by **Vineet Kaul**:
- Deploy Sample Agent App (A365) Guide
- A365 Workshop Pre-Requisites Guide
- Test Sample Agent App (Local) Guide

Uses Microsoft Learn documentation via MCP for up-to-date context.

## Version

**0.75 (Rohini)** — 08 Apr 2026

> *Named after ISRO's first indigenous rocket, the RH-75 (Rohini-75), launched 20 November 1967 from Thumba. Every journey begins with a first flight.*

## Roadmap — v1.00 (Rohini-100)

> *Named after ISRO's second indigenous rocket, the RH-100.*

Planned for the next release:
- Automated WAM browser auth handling to eliminate hidden sign-in windows
- `a365 cleanup` support for tearing down failed deployments
- Local agent testing via the Test Sample Agent App (Local) Guide before deploying to Azure
- Post-deployment health-check that queries Web App logs to confirm the agent is responding
