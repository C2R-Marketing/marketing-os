# Contributing

PRs welcome, with two hard rules:

1. **Markdown only.** This skill is deliberately free of executable code,
   scripts, and dependencies — that is what makes it trustable without review
   in any host (Claude, Codex, Cursor). PRs adding executable code will be
   declined regardless of quality.
2. **Match the spine.** Every module scores what it can, ships artifacts
   instead of advice, and states what it couldn't determine. Additions that
   hand back unscored opinions don't fit here.

Small fixes (broken cross-references, stale platform facts, deprecated
engine behavior) are the most valuable PRs — platform reality changes on a
scale of weeks and the modules say so.
