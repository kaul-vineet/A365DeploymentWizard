# CAPE Tutorial: Deploy A365 Agent

> Your personal guide through the full Microsoft Agent 365 deployment — from
> prerequisites to a live agent in Teams, with Defender observability and
> Copilot Studio MCP integration.

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
- Deploy Sample Agent App (A365).pdf
- A365 Workshop Pre-Requisites Guide.pdf

Uses Microsoft Learn documentation via MCP for up-to-date context.
