# Step-by-Step: Running a Persona in Claude Desktop

The hand-holding walkthrough. Every click, every paste, in order.
If you only need the short version, the README's Quick Start is that. This is the long one.

**Verified against Anthropic's help center (support.claude.com, "How can I create and manage projects?", September 2026).** UI labels can shift between Claude updates — if a button name doesn't match, look for the closest-named thing; the flow is stable.

---

## Part 0 — Pick your path

| You have… | Use | Section |
|---|---|---|
| Claude Pro / Team / Enterprise, want the persona everywhere | **Projects** | Part 1 |
| Any plan (incl. free), want to try a persona casually | **Custom Styles** | Part 4 |
| A team on Team/Enterprise, one canon persona for everyone | **Projects + Share** | Part 1 + Part 3 |
| Claude Code users instead of Claude Desktop | **CLAUDE.md** | Part 5 |

---

## Part 1 — Create the project and install the persona

1. Open Claude (claude.ai or the desktop app) and log in.
2. In the left sidebar, click **Projects**.
3. Click **New project** (or **Create project**, depending on the build).
4. Name it after the persona — `Thinker`, `Coach`, or `Daemon` — and pick a distinct accent color if prompted. The name is what you'll click every day; make it obvious.
5. You're now on the project's main page. Find **Set project instructions** and click it.
6. Open the persona file you chose (`02-persona-daemon.md`, `03-persona-thinker.md`, or `04-persona-coach.md` — copy it from this repo).
7. **Select all → copy → paste the entire file** into the instructions box. Don't trim it. The INTEGRITY section and the drop-in precedence rules at the bottom are functional, not decoration.
8. Click **Save instructions**.

**Checkpoint:** the project page should now show your instructions saved. Start a test chat from inside the project (click the project, then start a chat there — *not* from the main chat list). Say "morning." If the reply sounds like a person instead of a helpdesk, the persona took.

**If the reply is still assistant-flavored:** check you pasted the *whole* file, and check you're chatting *inside the project*, not in a regular chat with the project open in another tab. Instructions only apply to chats created within the project.

---

## Part 2 — Add the drop-in files (optional but recommended)

1. On the project's main page, find the **project knowledge** panel (right side).
2. Click **+** to add content.
3. Upload any of these, filled in first — see each template's header comments:
   - `05-dropin-voice-examples-template.md` → save it as `voice-examples.md` after filling in
   - `06-dropin-relationship-template.md` → save as `relationship.md`
   - `07-dropin-style-tweaks-template.md` → save as `style-tweaks.md`
4. Start a new chat inside the project and confirm the layer took (e.g. if your `style-tweaks.md` bans a word, get the persona to almost say it and see if it dodges).

**How the layers resolve** — you don't need to do anything, this is handled by the precedence rules inside every persona file:

```
style-tweaks.md        → wins over everything
voice-examples.md      → replaces the persona's built-in dialogue examples
relationship.md        → standing context about who it's talking to
persona file           → the base everything else layers onto
```

Missing file = that layer just doesn't exist. The persona works fine with zero drop-ins.

**Order of operations tip:** write `relationship.md` *first* (it's one page, highest impact per minute spent), then calibrate `voice-examples.md` over a week of real use, then add `style-tweaks.md` only when you notice a specific behavior you want dead.

---

## Part 3 — Share with the team (Team/Enterprise plans)

1. Open the project.
2. Click **Share project** (right of the project name).
3. Add coworkers by name or email — or paste a bulk list.
4. Set each person's permission:
   - **Can view** — they chat with the persona, can't edit it. **This is the one you want for rollout.**
   - Can edit — they can change instructions and knowledge. For co-maintainers only.
5. Click **Share**.

Coworkers find it under **Projects → Shared with you**. They chat with your canon persona — no copy-paste, no drift, one source of truth.

**Free/Pro plan workaround:** each person makes their own project (Part 1 takes two minutes, done once). If you edit the canon persona later, paste the updated file in the team channel and everyone re-pastes. This is the copy-paste drift problem — live with it or upgrade the plan.

---

## Part 4 — The lighter path: Custom Styles

No project, no knowledge files, no memory. Just a voice you can toggle onto any chat.

1. Open any chat.
2. Click the **+** menu in the composer → **Use style** → **Create & edit styles** → **Create custom style**.
3. Either paste the persona file as the style prompt, or click **Add writing example** and feed it the dialogue pairs from `voice-examples.md` (Claude builds the style from the examples).
4. Name it after the persona. Save.
5. Toggle it on/off per chat from the same **Use style** menu.

**When to use this instead of a project:** testing a persona for a week before committing, or when you only want the persona's voice in specific conversations. **What you give up:** no knowledge files, no drop-in layering, no team sharing, no per-project memory.

**Recommended rollout: Styles first, then Projects.** Let each coworker run the persona as a Style for a week. The ones who keep toggling it on are the ones who'll actually use the project.

---

## Part 5 — Claude Code users

Drop the persona file into the repo root as `CLAUDE.md`. Same effect as project instructions, scoped to that codebase, zero Claude-settings work. The drop-in files layer on top the same way if you `@`-mention or include them.

---

## Part 6 — Maintenance

**Updating the persona:** edit the project instructions — every future chat in that project picks it up immediately, no re-creation needed. Keep the canonical `.md` files version-controlled in this repo; after an edit, re-paste into any project that uses it.

**Persona drifting assistant-ward over long chats:** start a fresh chat inside the project. Long conversations dilute any instruction set. If it persists, the examples are too generic — sharpen `voice-examples.md`.

**Persona too aggressive / too soft:** that's a `style-tweaks.md` job, not a core edit. Add one line naming the behavior, e.g. *"If my message is under ten words, your reply stays under thirty."* Specific rules beat adjectives.

**Someone stacked two personas in one project:** delete one. They fight, and the result is neither.

---

## Troubleshooting quick table

| Symptom | Cause | Fix |
|---|---|---|
| Persona doesn't appear at all | Chat started outside the project | Start the chat *inside* the project |
| Sounds assistant-y | Pasted a trimmed version / examples too generic | Re-paste whole file; calibrate `voice-examples.md` |
| Drops persona after many turns | Normal long-chat drift | New chat in the same project |
| Ignores your style rules | Rule too vague for a rule | Move it to a concrete rule in `style-tweaks.md` |
| Two personas blended | Stacked in one project | One persona = one project. Delete one. |
| Coworker can't see shared project | Wrong tab or wrong permission | **Projects → Shared with you**; check they were given at least `Can view` |