# Deploying the Personas in Claude Desktop

Verified against Anthropic's help center (support.claude.com, "How can I create and manage projects?", Sept 2026).
Claude has **no system-prompt switching** and **no prompt library** — the real mechanisms are:

| Claude feature | Scope | Best for | Plan |
|---|---|---|---|
| **Project instructions** | Every chat in that project, persists | **The personas** — this is the main path | Pro / Team / Enterprise |
| **Custom Styles** ("Use style" in the composer) | Any single chat, one click | Voice-only tweaks / trying a persona casually | All plans (incl. free) |
| **Custom instructions** (Settings → Profile) | Every chat on the account | Never — one persona would poison everything | All plans |

**Rule of thumb: one persona = one project.** Don't stack two personas in one project's instructions.

---

## Path A — Projects (recommended)

1. In Claude, click **Projects** → **New project** → name it after the persona (e.g. `Thinker`).
2. Click **Set project instructions** → paste the full contents of the persona file (`02`–`04`).
3. **Save instructions.**
4. (Optional) Click **+** in the project knowledge panel → upload any drop-in files:
   `voice-examples.md`, `relationship.md`, `style-tweaks.md`.
   Knowledge files are read as context — the drop-in precedence rules inside each persona handle which layer wins.
5. Start all chats **from inside the project**. Instructions apply to every conversation there, and the project keeps its own memory separate from your other chats.

**Team sharing (Team/Enterprise plans only):** open the project → **Share project** → add coworkers by email → permission `Can view` (they chat with the persona but can't edit it). This is the cleanest way to distribute one canon persona to several people — one source of truth, no copy-paste drift.

**Free/Pro plan, no sharing:** each person creates their own project and pastes the persona file. Two minutes, done once.

## Path B — Custom Styles (lighter, per-chat)

1. Open any chat → **+** menu → **Use style** → **Create & edit styles** → **Create custom style**.
2. Paste the persona file as the style prompt, or use **Add writing example** and feed it dialogue pairs from `voice-examples.md`.
3. Toggle the style on/off per chat from the same menu.

Trade-offs vs Path A: no knowledge files, no shared memory, no team sharing — it's voice without infrastructure. Good for testing a persona before committing it to a project.

## Updating a persona later

Edit the project instructions — every future chat in that project picks it up immediately.
Version-control your canonical copies (the `.md` files in this kit) somewhere shared; re-paste after edits.

---

## What I'd fix before rollout

1. **Write a real `relationship.md` before sharing** — it's the layer that stops the persona from talking to an accountant like a junior dev.
2. **Calibrate `voice-examples.md` with real phrasing from the people who'll talk to it.** Examples are the highest-leverage part of these prompts; Claude copies them more faithfully than it obeys abstract rules.
3. **Don't put persona text in account-level custom instructions** — it bleeds into every chat and there's no per-chat off switch.
4. **Keep the INTEGRITY section.** It's what keeps the companion voice from drifting into the model pretending to be human.
5. If anyone uses **Claude Code** rather than Claude Desktop: put a persona file in the repo as `CLAUDE.md` — same effect, scoped to that codebase.

---