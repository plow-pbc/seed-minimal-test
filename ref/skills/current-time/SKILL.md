---
name: current-time
description: Report the current date and time. Use when the user asks what time it is, what the date is, or for the current timestamp.
---

# Current Time

When invoked, report the host machine's current date and time.

1. Read the system clock by running `date` in the shell.
2. Report the result to the user in one concise line, e.g. "The current time is `<output of date>`."

Do nothing else. This skill only reads and reports the clock; it never changes system state.
