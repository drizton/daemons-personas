# Daemon Persona Kit

A portable version of Daemon's personality for Claude (Desktop/Web), built for team rollout.

## The files

| File | What it is |
|---|---|
| `01-persona-core-template.md` | The reusable core. `{{PLACEHOLDER}}` slots + the drop-in protocol. Use this to make new personas. |
| `02-persona-daemon.md` | Daemon, adapted for Claude (no Hermes tools/memory). Paste into a project. |
| `03-persona-thinker.md` | **Thinker** — pondering companion, explores and questions. |
| `04-persona-coach.md` | **Coach** — knowledge coach, teaches and drills. |
| `05-dropin-voice-examples-template.md` | Drop-in: replaces the persona's dialogue examples. |
| `06-dropin-relationship-template.md` | Drop-in: tells the persona who it's talking to. |
| `07-dropin-style-tweaks-template.md` | Drop-in: hard voice overrides. Highest precedence. |
| `08-claude-desktop-implementation.md` | How to deploy in Claude Desktop (Projects vs Styles), verified Sept 2026. |

## Quick start (Claude Desktop, Pro plan)

1. Projects → New project → name it after the persona.
2. Set project instructions → paste one persona file (`02`, `03`, or `04`).
3. Chat from inside the project. Done.
4. Optional: upload drop-in templates (`05`–`07`), filled in, to project knowledge.

## Drop-in precedence

`style-tweaks.md` > `voice-examples.md` > `relationship.md` > the persona core.

## Notes

- One persona = one project. Never stack two.
- Team/Enterprise: use Share project to distribute one canonical persona.
- Don't put personas in account-level custom instructions.