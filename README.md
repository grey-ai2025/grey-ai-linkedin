# Grey AI — LinkedIn Content Engine

AI-assisted LinkedIn content generator for Grey AI. Uses Claude Code + a custom LinkedIn scraper MCP to research competitors, analyze engagement trends, and draft posts in Grey AI's voice.

---

## Prerequisites

Install these before cloning:

| Tool | Install |
|------|---------|
| **Python 3.12+** | [python.org](https://www.python.org/downloads/) |
| **uv** (Python package manager) | `pip install uv` or `winget install astral-sh.uv` |
| **Node.js** (LTS) | [nodejs.org](https://nodejs.org/) |
| **Claude Code CLI** | `npm install -g @anthropic/claude-code` |
| **VS Code** | [code.visualstudio.com](https://code.visualstudio.com/) |
| **Claude Code VS Code extension** | Search "Claude Code" in VS Code Extensions panel |

---

## Setup

### 1. Clone the repo

```bash
git clone https://github.com/YOUR_USERNAME/grey-ai-linkedin.git
cd grey-ai-linkedin
```

### 2. Install LinkedIn scraper dependencies

```bash
uv sync --project linkedin-mcp-local
```

uv reads the `uv.lock` file and sets up the virtual environment automatically.

### 3. Install the Patchright browser

The scraper uses a Chromium browser to access LinkedIn. Install it once:

```bash
uv run --project linkedin-mcp-local patchright install chromium
```

### 4. Log into LinkedIn

```bash
uv run --project linkedin-mcp-local linkedin-mcp-server --login
```

A browser window will open. Log in with your LinkedIn account. The session is saved locally to `.linkedin-mcp/` (this folder is gitignored — each person has their own session).

### 5. Set your Anthropic API key

Get a key from [console.anthropic.com](https://console.anthropic.com). Then set it as an environment variable:

**Windows (PowerShell):**
```powershell
$env:ANTHROPIC_API_KEY = "sk-ant-..."
```

**Or add to a `.env` file in the project root:**
```
ANTHROPIC_API_KEY=sk-ant-...
```

### 6. Create your local Claude permissions file

This file is gitignored (each person has their own). Create it at `.claude/settings.local.json`:

```json
{
  "permissions": {
    "allow": [
      "WebSearch",
      "mcp__linkedin-scraper__get_company_posts",
      "mcp__linkedin-scraper__get_company_profile",
      "mcp__linkedin-scraper__get_person_profile",
      "mcp__linkedin-scraper__get_person_posts"
    ]
  },
  "enabledMcpjsonServers": ["linkedin-scraper"]
}
```

### 7. Open the project and launch Claude Code

```bash
code grey-ai-linkedin
```

Then in the VS Code terminal:

```bash
claude
```

---

## How It Works

Claude follows the workflow defined in `CLAUDE.md`:

1. **Scrape** — Automatically iterates through all profiles in the watchlist, one at a time
2. **Analyze** — Compiles all findings into one research file, identifies top content and trends
3. **Draft** — Writes posts inspired by watchlist content, but in Grey AI's analytical voice
4. **Save** — Saves drafts to `drafts/YYYY-MM-DD-[slug].md` with copy-paste blocks

---

## Refreshing the LinkedIn Session

Sessions expire periodically. When they do, run:

```bash
uv run --project linkedin-mcp-local linkedin-mcp-server --login
```

Claude will ask you to refresh the session when it expires. It will retry once after you refresh. After two failed attempts, it will automatically fall back to web search.

**Other session commands:**
```bash
# Check if session is active
uv run --project linkedin-mcp-local linkedin-mcp-server --status

# Log out / clear session
uv run --project linkedin-mcp-local linkedin-mcp-server --logout
```

---

## Project Structure

```
grey-ai-linkedin/
├── CLAUDE.md                  # Full workflow, voice guide, content rules
├── .mcp.json                  # MCP server config (LinkedIn scraper)
├── competitors/
│   └── watchlist.md           # Competitor list with research prompts
├── drafts/                    # Generated post drafts (YYYY-MM-DD-slug.md)
├── research/                  # Competitor analyses and trend findings
└── linkedin-mcp-local/        # Custom LinkedIn scraper MCP server (Python)
```
