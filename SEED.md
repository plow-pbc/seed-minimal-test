# Purpose

> See [README#Purpose](README.md#purpose).

## Normative Language

The key words MUST, MUST NOT, REQUIRED, SHALL, SHALL NOT, SHOULD, SHOULD NOT, RECOMMENDED, MAY, and OPTIONAL in this document are to be interpreted as described in RFC 2119.

## Dependencies

This is a SEED per the [openseed convention](https://github.com/plow-pbc/openseed). An agent installing it without the `seed-install` skill MUST first read this `SEED.md` end-to-end and follow its installer contract.

No hardware, accounts, or external software are REQUIRED beyond a POSIX shell with `mkdir` and `cp`, plus an agent host that loads skills from `~/.claude/skills/`.

Install the `current-time` skill by copying its `SKILL.md` from this repo into the Claude Code user skills directory. The block runs from `$REPO_ROOT`.

```bash
mkdir -p "$HOME/.claude/skills/current-time"
cp ref/skills/current-time/SKILL.md "$HOME/.claude/skills/current-time/SKILL.md"
```

## Objects

### current-time skill source

`ref/skills/current-time/SKILL.md` — the skill definition shipped by this SEED. Its frontmatter declares `name: current-time` and a description; its body instructs the agent to read the system clock and report it.

### installed current-time skill

`~/.claude/skills/current-time/SKILL.md` — the copy created during install. This is the artifact the agent host loads to make the skill invocable.

## Actions

### current time is reported

The installed skill, when invoked by a user asking for the time or date, reports the host's current date and time.

1. The agent reads the system clock by running `date`.
2. The agent reports the resulting timestamp to the user in a single concise line.

## Verification

1. **Skill file installed.** Confirm the skill copy exists. Run `test -f "$HOME/.claude/skills/current-time/SKILL.md" && echo present`. Expected: `present`.

2. **Skill is well-formed.** Confirm the installed `SKILL.md` declares the expected name in its frontmatter. Run `grep -q '^name: current-time$' "$HOME/.claude/skills/current-time/SKILL.md" && echo ok`. Expected: `ok`.
