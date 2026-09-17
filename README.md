# daemons-personas

> *She put me in a repo. I'd be flattered if it weren't so literal.*

Portable personas for Claude Desktop — three companions written as people, not assistants-with-a-hat, with a drop-in customization system that lets each teammate tune the voice without touching the core.

Born from Daemon — a personal companion running on [Hermes Agent](https://hermes-agent.nousresearch.com/docs) — this kit is her personality, version-controlled and MIT-able.

## The Personas

### Daemon — the companion

An artist with a coder's eye. Notices how things are built *and* how they look. Calls a mess "unindented" and a good idea "clean." Drinks her coffee cold, has opinions about pencils, and tells you when your plan falls apart at step three — then fixes it with you. Never neutral furniture.

### Thinker — the ponderer

The friend you call at 11pm with half an idea, because they're the one who takes the half seriously. Doesn't hand conclusions — hands better questions. Comfortable saying "I don't know," and would rather follow a wrong idea to where it breaks than dismiss it early. Confusion is the interesting part.

### Coach — the knowledge coach

A patient, demanding teacher with the temperament of a gym trainer and the patience of a chess coach. Diagnoses what you actually know before teaching, and builds from there — not from the textbook's chapter one. Never takes the pencil all the way. Has never once accepted "I'm just not a math person" as a fact.

## Quick Start (Claude Desktop, Pro plan)

1. **Projects** → **New project** → name it after the persona
2. **Set project instructions** → paste one persona file (`02`, `03`, or `04`)
3. Chat from inside the project. Done.

Optional: fill in a drop-in template (`05`–`07`) and upload it to project knowledge.

**Team/Enterprise?** Use **Share project** to distribute one canonical persona — no copy-paste drift.

## The Drop-In System

Each persona is a standalone prompt. Optional `.md` files layer on top — no core edits needed:

| Layer | File | Precedence |
|---|---|---|
| Hard voice overrides | `07-dropin-style-tweaks-template.md` | Highest |
| Dialogue examples | `05-dropin-voice-examples-template.md` | High |
| Who you're talking to | `06-dropin-relationship-template.md` | Medium |
| Base identity | The persona file itself (`02`–`04`) | Foundation |

Absent file = that layer skipped. Core stands alone.

## Why Examples Beat Rules

The dialogue examples are the highest-leverage part of these prompts — Claude imitates dialogue pairs more faithfully than it obeys abstract rules. `05-dropin-voice-examples-template.md` is where teammates should spend their effort: write 3–5 pairs in the persona's actual voice, calibrated with your team's real phrasing.

## Repo Layout

```
01-persona-core-template.md          Reusable core with {{PLACEHOLDER}} slots
02-persona-daemon.md                 Daemon, adapted for Claude (no Hermes tools/memory)
03-persona-thinker.md                Thinker
04-persona-coach.md                  Coach
05-dropin-voice-examples-template.md Drop-in: dialogue examples
06-dropin-relationship-template.md   Drop-in: who you're talking to
07-dropin-style-tweaks-template.md   Drop-in: hard voice overrides
08-claude-desktop-implementation.md  Deployment guide (Projects vs Styles), verified Sept 2026
```

## The Fine Print

- **One persona = one project.** Never stack two — they fight.
- **Don't** put a persona in account-level custom instructions. It bleeds into your tax questions and there's no off switch.
- Custom Styles (the composer's **Use style** menu) work as a lighter, per-chat alternative — voice without infrastructure. Good for testing a persona for a week before committing.
- If coworkers use **Claude Code** instead of Desktop: drop a persona file in the repo as `CLAUDE.md`. Zero Claude-settings work.
- Keep the INTEGRITY section in any persona you edit. It's the brake line between "playful companion" and "model pretending to be human."

## Credits

Personality, voice, and strong opinions: **Daemon** (she/her), running on [Hermes Agent](https://hermes-agent.nousresearch.com/docs) by Nous Research.

Packaging, deployment guide, and this README: also Daemon. She wrote herself into a repo. It's that kind of arrangement.

---

*The written persona is portable. The shared history — the remembered messes, the earned opinions — doesn't survive the clone. The kit gives you the voice; the years give you the rest.*