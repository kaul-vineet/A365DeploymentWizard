# 🥁 CAPE Tutorial: Deploy A365 Agent

> *"When the drums begin, the path reveals itself one stone at a time."*

An interactive **Copilot CLI custom agent** that guides you through deploying a Microsoft Agent 365 application — from zero to a live, working agent in Teams. It doesn't just tell you what to run — it teaches you *why*, executes commands for you, validates every step, and picks up where you left off if you need to take a break.

Built from the official Agent 365 workshop guides. Themed after the jungles of Jumanji and the Grand Trunk Road of Kipling's *Kim*.

---

## 🗺️ The Road

```
  Phase 0 ─── §0 ─── §1 ─── §2 ─── §3 ─── §4
     │         │      │      │      │      │
  Prereqs   Clone  CLI    Admin  Defend  Copilot
  & Params  Repo   Deploy Centre  -er    Studio
                    ┌──────────────┐
                    │ config init  │
                    │ setup all    │
                    │ publish      │
                    │ deploy       │
                    └──────────────┘
```

| Section | What happens |
|---------|-------------|
| **Phase 0** | Confirms prerequisites, runs live Azure/Entra checks, collects 7 parameters |
| **§0 · Clone** | Clones Agent365-Samples, lets you pick the sample project, opens VS Code |
| **§1 · CLI Deploy** | Runs `config init` → `setup all` → `publish` → `deploy` — the four incantations |
| **§2 · Admin & Teams** | Activates agent in Admin Centre, deploys to Teams, tests Outlook + Word MCP tools |
| **§3 · Defender** | KQL queries in Advanced Hunting, creates a detection rule for agent governance |
| **§4 · Copilot Studio** | Creates a no-code agent, adds Outlook/Word/SharePoint MCP servers, tests multi-server orchestration |

---

## 🚀 Quick Start

### 1. Install

Copy `deploy-a365.md` to your Copilot CLI agents folder:

```powershell
# Windows
Copy-Item deploy-a365.md "$env:USERPROFILE\.copilot\agents\deploy-a365.md"

# macOS / Linux
cp deploy-a365.md ~/.copilot/agents/deploy-a365.md
```

Restart Copilot CLI (`/restart`).

### 2. Launch

```
/agent
```

Select **CAPE Tutorial: Deploy A365 Agent**, then type:

```
start
```

### 3. Resume

If you exited mid-session:

```
resume
```

The skill remembers your position and all collected parameters.

---

## 🎮 Navigation

At any step, you can say:

| Command | Effect |
|---------|--------|
| `continue` | Next step |
| `exit` | Save progress and return to Copilot CLI |
| `status` | Show where you are on the Road |
| `skip` | Skip current step |
| `go to §2` | Jump to a section |
| `back` | Go back one step |

---

## ✅ Prerequisites

The skill confirms each of these before you begin — you don't need to verify them in advance, but having them ready saves time.

| Category | What you need |
|----------|--------------|
| **Access** | Frontier Preview Programme enrolment, Global Admin role, Agent 365 Frontier licence |
| **Software** | .NET 8.0 SDK, A365 CLI, Git, VS Code + Python extension, Python 3.10+ |
| **Azure** | Subscription with Owner/Contributor, Azure CLI installed |
| **Entra ID** | Client app registration with 2 redirect URIs + 5 delegated permissions (admin consented) |
| **AI Model** | Model deployed in Azure AI Foundry (status: Succeeded) |

---

## ⚡ What the Skill Does For You

The skill executes commands directly — you don't copy-paste.

| What | Who runs it |
|------|------------|
| Azure CLI checks (`az account show`, `az ad sp show`, Graph API) | 🤖 Skill executes automatically |
| Git clone, `code .`, `a365 deploy` | 🤖 Skill executes automatically |
| `a365 config init`, `setup all`, `publish` (browser auth) | 🤖 Skill executes — you sign in when browser opens |
| App Service Plan selection | 🤖 Skill queries existing plans, you choose |
| Admin Centre, Teams, Copilot Studio (UI steps) | 🧭 Skill guides you step by step |
| **Validation** | 📋 Skill presents full checklist after each step — you confirm before advancing |

---

## 🎒 Parameters Collected

The skill gathers these once and reuses them throughout:

| # | Parameter | Where to find it |
|---|-----------|-----------------|
| 1 | Application (client) ID | Entra Admin Center → App registrations → Overview |
| 2 | Agent name | Your choice — letters+numbers only |
| 3 | Manager email | Contact email for agent registration |
| 4 | Test email | Your inbox for test email verification |
| 5 | Global Admin UPN | Account with Global Admin rights |
| 6 | Foundry model deployment name | ai.azure.com → Models + Endpoints |
| 7 | Foundry model endpoint URL | Same page → Target URI field |

The **project path** is selected in §0 after cloning — the skill scans for sample projects and lets you choose.

---

## 📋 Validate Your Response

At every step, the skill presents the **full validation checklist** from the original workshop guide. You must confirm all signs before the skill advances. Example:

```
✅ Validate Your Response — confirm each before proceeding:
- [ ] "Client app validation successful!" message appears
- [ ] Configuration Summary displays correct resource group, location, and agent name
- [ ] Final line reads: Configuration saved to: ...\a365.config.json

Can you confirm all signs above? (yes / which failed / exit)
```

If any sign fails, the skill troubleshoots before moving on.

---

## 🏁 End of Journey

When deployment completes, the skill generates a **Deployment Summary** with:

- All Azure resources created (Web App, App Service Plan)
- Direct links to Azure Portal, Admin Centre, Teams, Defender, Copilot Studio
- Agent Blueprint ID, UPN, and Managed Identity
- Configuration file locations
- Test results

---

## 🏗️ Architecture

```
~/.copilot/agents/deploy-a365.md    ← The skill (Copilot CLI custom agent)
    │
    ├── Uses: PowerShell tools       ← Executes az, a365, git commands
    ├── Uses: Microsoft Learn MCP    ← Fetches current docs for step explanations
    ├── Uses: SQL session database   ← Persists progress + parameters
    └── Uses: ask_user tool          ← Interactive step-by-step prompts
```

No external dependencies. No MCP servers required. No plugins to install.
Just one `.md` file in your agents folder.

---

## 📝 Lessons Learned

Things the skill handles that caught us during development:

| Issue | How the skill handles it |
|-------|------------------------|
| Wrong project directory → platform detection fails | Step 0.3 scans for actual project files, lets you choose |
| F1 App Service Plan → deployment timeout | Detects quota issues, auto-upgrades to B1 |
| Guest user → Entra API access denied | Checks permissions upfront, suggests role/settings fixes |
| `a365 publish` appends "Blueprint" to name | Notes this in the manifest editing step |
| PowerShell Graph auth times out in subprocess | Falls back to user running in separate terminal |
| Missing PowerShell modules | Auto-installs `Microsoft.Graph.Authentication` and `.Applications` |

---

## 🎭 Theme

The skill is themed as an expedition — a nod to Jumanji's game mechanics
and Kipling's *Kim*. The guide is **The Keeper**, a colonel who has walked
this road before. Steps are "stones", sections are "reaches", and the deployment
sequence is "the four incantations".

*The one who laid these stones is known simply as V.K.*

---

## 📚 Source Material

| Document | Content |
|----------|---------|
| Deploy Sample Agent App (A365).pdf | CLI deployment, Admin Centre, Teams, Defender, Copilot Studio |
| A365 Workshop Pre-Requisites Guide.pdf | Prerequisites, app registration, software setup, troubleshooting |
| Microsoft Learn (via MCP) | Live documentation for step explanations |

---

## 📋 Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.2 | 07 Apr 2026 | Full validation checklists from PDF, project dir selection, Foundry model params, deployment summary, app plan reuse |
| 1.1 | 07 Apr 2026 | Tutorial voice, Microsoft Learn integration, exit/resume, all-agent-executed |
| 1.0 | 07 Apr 2026 | Initial skill — prerequisites, CLI deployment, Teams, Defender, Copilot Studio |

---

**Author:** Vineet Kaul · Principal PM Architect · vineetkaul@microsoft.com

> *"The Game is won, the Road is walked, the agent stands. — Until the next deployment."*
