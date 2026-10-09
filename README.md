# downsizing-site

A Claude Code skill that launches a complete "<City> Downsizing" lead-generation website for a new city, end to end: scaffold, state-law research, neighborhoods, 55+ communities and guides, photos, SEO, Cloudflare Pages deploy, domain, lead email, indexing, and blog guides.

## Requirements

- [Claude Code](https://claude.com/claude-code)
- `git`
- A Cloudflare account (the skill deploys to Cloudflare Pages)

## Install

```bash
git clone https://github.com/KCDryan/downsizing-site.git ~/.claude/skills/downsizing-site
```

Restart Claude Code (or start a new session) so it picks up the skill.

## Use

In Claude Code, type:

```
/downsizing-site
```

or just say "launch a downsizing site for Denver". Claude will ask once for anything missing:

- City, state, state abbreviation, core county
- Brokerage
- Lead email (a real external inbox)
- Whether the team is licensed in that state
- Whether the domain is bought and on Cloudflare
- Colors (optional)

Then it follows the full procedure in `SKILL.md`, stopping only where a step says to ask.

## Update

```bash
git -C ~/.claude/skills/downsizing-site pull
```

## Contents

- `SKILL.md`: the step-by-step procedure
- `references/`: briefs for the site, neighborhoods/boroughs and blog guides
