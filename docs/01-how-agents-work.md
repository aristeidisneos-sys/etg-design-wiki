# 01 · How agents work

> **Goal:** Get the mental model, pick the right tool, and get a first win in 15 minutes.
> **Level:** Beginner · **Time:** 10 min read + 15 min exercise

---

## 1. The mental model

An AI agent isn't a smarter autocomplete. It's a **new teammate who is fast, tireless, and starts every task knowing nothing about your team.**

Results depend on three things you control:

| Ingredient | Question it answers | Example |
|---|---|---|
| **Context** | What does "good" look like here? | Our design system, naming rules, a reference screen |
| **Constraints** | What must it use, and what must it avoid? | Library components only, no hardcoded values, don't touch locked pages |
| **Verification** | How do we know it worked? | Screenshot check, re-audit, side-by-side with the brief |

Weak output almost always traces back to one of these being missing. Before blaming the model, ask which one you left out.

### Three habits that matter more than any prompt trick

1. **Small steps.** Ask for one section, one component, or one audit. Review it, then continue.
2. **Plan before action.** For anything non-trivial, ask: *"Tell me your plan first. Don't change anything yet."*
3. **You review, always.** The agent is fast; you are accountable. Treat its output like a junior designer's first pass.

---

## 2. Which tool for which job?

| You want to… | Use | Why |
|---|---|---|
| Design or edit **inside Figma**, with the canvas in front of you | **Figma's built-in AI / agents** | Closest to the canvas; good for quick, visual iteration |
| Let Claude **read from or write to a Figma file** (generate screens, audit, tidy up) | **Claude + Figma MCP** (Claude desktop / Cowork, or Claude Code) | Agent works on real files using your design system |
| **Turn designs into code**, or work in a repo | **Claude Code** | Reads your codebase and Figma together; can run and test |
| Write briefs, research, plan, draft docs, think out loud | **Claude chat** | Best for ideas and text before you touch a file |
| Repeat the same job the same way every time | **Skills** (shared, reusable instructions) | Encodes team standards so everyone gets the same result |

!!! note "Keep it simple at first"
    Start with **one** tool and **one** workflow. Most people get more value from going deep on one than from trying everything.

!!! warning "Verify against current docs"
    Figma's AI features and the MCP server change quickly. Check Figma's and Anthropic's documentation for what's available on your plan before you rely on a feature.

---

## 3. One-time setup checklist

- [ ] Claude access (desktop app, or Claude Code installed)
- [ ] Figma connector / MCP server connected and authorised
- [ ] Access to the team's Figma library (design system) in your account
- [ ] A **practice file**: a duplicate you can't hurt
- [ ] Read-only access first. Add edit access once you're comfortable.

If you get stuck, ask in the team channel and **write down what fixed it**. That's the first entry for the wiki.

---

## 4. Anatomy of a good request

Use this shape for almost everything. Missing parts are the usual cause of poor results.

```
GOAL        What I want, in one sentence.
CONTEXT     File/page link, audience, why it matters.
USE         Library, components, tokens, or a reference page to follow.
AVOID       What not to touch or invent.
OUTPUT      What I want back (a plan, a screen, a report, a list).
DONE WHEN   How we'll know it's right.
```

**Weak:**
> Make a settings page.

**Strong:**
> **Goal:** Draft a "Notification settings" page for the web app.
> **Context:** Logged-in user, desktop. Page link: `<link>`.
> **Use:** Only components from our design system library. Follow the layout of the "Account settings" page.
> **Avoid:** New components, hardcoded colours or spacing.
> **Output:** First give me a short plan (sections and which components). Wait for my OK, then build.
> **Done when:** Everything is bound to variables, layers are named, and you've shown a screenshot.

More patterns live in [02 · Prompting & context](02-prompting-and-context.md).

---

## 5. Your 15-minute first win

Goal: see the full loop of **ask → plan → review → verify** on something harmless.

**Setup:** Open your practice file (a duplicate). Connect Claude to it.

### Step 1 · Read-only audit (5 min)
Paste:
```
Look at <practice page link>. Don't change anything.
List: (1) layers with default names like "Frame 123",
(2) fills or text that aren't bound to variables or styles,
(3) anything that looks like a detached component.
Give me counts and a few examples of each.
```
**Check:** Are the counts plausible? Open two of the examples in Figma to confirm they're real.

### Step 2 · Plan, then a small fix (5 min)
Paste:
```
Propose renames for the 10 worst-named layers as a table (current → proposed).
Follow the pattern "Role – detail" (e.g. "Header", "Price row").
Wait for my approval.
```
Edit the table if you disagree, then reply: *"Apply these 10 renames only."*

### Step 3 · Verify (5 min)
Paste:
```
Take a screenshot of the page and confirm the 10 renames were applied.
List anything you changed that I did not approve.
```
**Check:** The answer to the last line should be "nothing."

### What you just practised
Audit before changing, small scope, approval gate, verification. That's the loop behind every workflow in this wiki.

---

## 6. Do's and don'ts

| Do | Don't |
|---|---|
| Point to real pages and components as references | Describe your design system from memory |
| Ask for a plan before big changes | Let it modify a whole file in one go |
| Work on duplicates for anything risky | Experiment in production files |
| Ask "what did you change that I didn't ask for?" | Assume silence means nothing extra changed |
| Save prompts that worked | Re-invent them each time |
| Share what you learn with the team | Keep tricks to yourself |

---

## 7. Where to go next

| If you want to… | Read |
|---|---|
| Write better requests | [02 · Prompting & context](02-prompting-and-context.md) |
| Make your files "agent-readable" | [03 · Design system hygiene](03-design-system-hygiene.md) |
| Create screens from a brief | [05 · Brief to Figma](05-brief-to-figma.md) |
| Create components from a rough draft | [06 · Components from a draft](06-components-from-draft.md) |
| Keep files clean with less effort | [07 · Tidy up](07-tidy-up.md) |
| Avoid common mistakes | [08 · Pitfalls & verification](08-pitfalls-and-verification.md) |

---

## 8. Glossary

| Term | Meaning |
|---|---|
| **Agent** | An AI that takes multi-step actions (reads, plans, edits, checks), not just answers |
| **MCP** | A standard way to connect an AI to tools such as Figma |
| **Claude Code** | Claude in the terminal or IDE, working with files and code |
| **Skill** | Saved, reusable instructions that make the agent follow a team standard |
| **CLAUDE.md** | A project file Claude Code reads automatically for rules and context |
| **Code Connect** | Figma's mapping between design components and code components |
| **Variable / token** | A named design value (colour, spacing, radius) used instead of a raw number |
| **Context** | Everything the agent knows for the current task |

---

*Version 0.1 · Draft. Add your own lessons below.*

### Changelog
| Date | Change | By |
|---|---|---|
| 2026-10-07 | Initial draft | |
