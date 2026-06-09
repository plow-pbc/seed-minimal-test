# seed-minimal-test

A minimal SEED that installs a single "current-time" agent skill. Built to be the fastest possible SEED to install — a smoke-test fixture for the SEED lifecycle.

## Purpose

`seed-minimal-test` is the smallest useful SEED: installing it drops one agent skill onto your machine that, when invoked, reports the host's current date and time. It exists as a fast, low-footprint fixture for automated testing of the SEED install/verify lifecycle — it requires no hardware, accounts, or external software, touches only a single file under your skills directory, runs in well under a second, and cleanly verifies. Use it to smoke-test a `seed-install` implementation end to end without cloning a heavy real-world project.

## Install

If your agent already has the `seed-install` skill, point it at this repo:

> Install `<this-repo-url>`

The agent clones the URL, reads [`SEED.md`](SEED.md), runs the one `## Dependencies` shell block (which copies the skill into your Claude Code user skills directory), then answers the `## Verification` prompts.

## What it installs

The `current-time` skill — a `SKILL.md` placed at `~/.claude/skills/current-time/`. The source ships in this repo at [`ref/skills/current-time/SKILL.md`](ref/skills/current-time/SKILL.md). Once installed, asking your agent "what time is it?" triggers the skill, which reads the system clock with `date` and reports the result.

## License

MIT.
