# Agent Lab Course Resources

Downloadable resources for courses on [Agent Lab](https://www.skool.com/agent-lab).

## Claude Code Fundamentals

### Agent Library

12 plug-and-play agents for Claude Code. Drop them into `.claude/agents/` in your project and they just work.

**Core Agents:**
- `frontend.md` - React/Next.js/Vue/Svelte UI specialist
- `backend.md` - API/server specialist (Node, Python, Go)
- `database.md` - Schema design, migrations, queries, optimization
- `build.md` - Build/lint/typecheck validation and fixing
- `reviewer.md` - Code review (read-only)
- `debugger.md` - Root cause analysis and minimal fixes
- `git.md` - Git operations, branching, PRs

**Deployment Agents:**
- `vercel.md` - Vercel deployment specialist
- `railway.md` - Railway deployment specialist
- `fly-io.md` - Fly.io deployment specialist
- `netlify.md` - Netlify deployment specialist
- `cloudflare.md` - Cloudflare Workers/Pages specialist

### How to Use

1. Download the `.md` files you need
2. Put them in `.claude/agents/` in your project (or `~/.claude/agents/` for all projects)
3. Start using Claude Code - it will automatically delegate to the right agent

Each agent has a self-customization section that scans your project on first run and adapts to your stack.
