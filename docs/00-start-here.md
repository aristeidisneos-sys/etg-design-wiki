# 00 · Start here

> **Goal:** Connect Claude to your Figma file and our team tools, then prove it works, without needing help.
> **Level:** Beginner · **Time:** about 20 min
> **Status:** <span class="status">Draft v0.1</span> Draft, validate with IT

!!! note "Don't have Claude Desktop installed?"
    [Download it here](https://claude.ai/download).

---

## Where are you?

| Your situation | Go to |
|---|---|
| Nothing set up yet | [Step 1 · Claude Desktop](#step-1-claude-desktop) |
| Claude is installed, no connectors yet | [Step 2 · Figma](#step-2-figma) |
| Everything is connected | [Verify everything](#verify-everything) |

## Connection checklist

- [ ] 1 · Claude Desktop installed and signed in with your company account: **Required**
- [ ] 2 · Figma: **Required**
- [ ] 3 · Google Drive (wiki, skills, registry): **Required**
- [ ] 4 · Atlassian: **Recommended**
- [ ] 5 · Slack (read-only): **Recommended**
- [ ] 6 · Gmail: **Optional**
- [ ] 7 · Google Calendar: **Optional**
- [ ] 8 · Team skills installed: **Recommended**
- [ ] 9 · Verification passed: **Required**

Copy this list into your notes and tick as you go (the boxes on this page are display only). If a connector needs admin approval, note it and move on.

---

## Before you start

| You need | How to check |
|---|---|
| A company Claude account | You can sign in to Claude Desktop with your work email |
| A Figma seat, with access to the team's design system library | You can open the library file in Figma |
| Access to the wiki and `Skills/` folders in Google Drive | You can open both folders in Drive |
| A practice file | A Figma file you can open and are happy to read from. Use a copy, never a shared production file |

---

## Step 1 · Claude Desktop

**Why connect it:** Everything else connects through it.

**What Claude can access:** Only what you type or attach in a conversation, until you connect tools in the next steps.

**Steps**

1. Install Claude Desktop using the download link at the top of this page.
2. Open the app and choose to sign in. (verify on first run)
3. Sign in with your **company** account, not a personal one. (verify on first run)

**What you should see:** The chat window, signed in with your company account.

!!! note "Screenshot needed"
    `assets/screenshots/claude-desktop/01-signed-in.png`: The Claude Desktop chat window after signing in, with the account name or email visible (blur anything private).

**Verification prompt** (read-only)

```
Say hello and tell me which model you are. Do not use any tools.
```

Last verified: not yet

---

## Step 2 · Figma

**Why connect it:** Lets Claude read your files, pages, components and variables.

**What Claude can access:** Files and libraries your Figma account can open. Claude works as you, so it can never see more than you can.

**Steps**

1. In Claude Desktop, open the settings and find the connectors list. (verify on first run)
2. Find **Figma** and select the option to connect it. (verify on first run)
3. Sign in with your company Figma account and approve access when asked. (verify on first run)
4. If asked which team or workspace to use, pick the one that holds our design system library. (verify on first run)

**What you should see:** Figma shown as connected in the connectors list.

!!! note "Screenshot needed"
    `assets/screenshots/figma/01-connector-list.png`: The connectors list in Claude Desktop with Figma shown as connected.

!!! note "Screenshot needed"
    `assets/screenshots/figma/02-authorise.png`: The Figma approval screen shown when connecting (before you approve).

**Verification prompt** (read-only)

```
Using the Figma connector, read-only: open <paste your practice file link> and tell me the file name and list the names of its pages. Do not change anything.
```

Last verified: not yet

---

## Step 3 · Google Drive

**Why connect it:** Home of the wiki, the team skills library (`Skills/` folder) and the page registry.

**What Claude can access:** Files your Google account can open. Avoid asking Claude to edit, move or share files unless you mean to.

**Steps**

1. In the connectors list, find **Google Drive** and select the option to connect it. (verify on first run)
2. Sign in with your company Google account. (verify on first run)
3. Approve the access request. (verify on first run)

**What you should see:** Google Drive shown as connected in the connectors list.

!!! note "Screenshot needed"
    `assets/screenshots/drive/01-connected.png`: The connectors list with Google Drive shown as connected.

**Verification prompt** (read-only)

```
Using Google Drive, read-only: give me the titles of up to 3 recently modified files in <paste the wiki or Skills folder name>. Do not open, edit, move or share anything.
```

Last verified: not yet

---

## Step 4 · Atlassian (Jira)

**Why connect it:** Figma agents already use it through our Jira connector, so tickets and designs stay linked.

**What Claude can access:** Jira projects and issues your Atlassian account can see.

**Steps**

1. In the connectors list, find **Atlassian** and select the option to connect it. (verify on first run)
2. Sign in with your company Atlassian account. (verify on first run)
3. Approve access to the Jira site when asked. (verify on first run)

**What you should see:** Atlassian shown as connected in the connectors list.

!!! note "Screenshot needed"
    `assets/screenshots/atlassian/01-connected.png`: The connectors list with Atlassian shown as connected.

**Verification prompt** (read-only)

```
Using the Atlassian connector, read-only: tell me how many Jira issues are assigned to me. Do not list titles. Do not create or change anything.
```

Last verified: not yet

---

## Step 5 · Slack (read-only)

**Why connect it:** Lets Claude find context from team discussions.

**What Claude can access:** **Read-only.** IT Ops sets this: Claude can read what your account can see and cannot post, react or send. Do not ask it to.

**Steps**

1. In the connectors list, find **Slack** and select the option to connect it. (verify on first run)
2. Sign in to the company workspace. (verify on first run)
3. Approve the read-only access request. If it asks for more than reading, stop and check with IT Ops. (verify on first run)

**What you should see:** Slack shown as connected in the connectors list.

!!! note "Screenshot needed"
    `assets/screenshots/slack/01-connected.png`: The connectors list with Slack shown as connected.

!!! note "Screenshot needed"
    `assets/screenshots/slack/02-permissions.png`: The Slack permission screen, showing that access is read-only.

**Verification prompt** (read-only)

```
Using Slack, read-only: tell me how many channels you can see. If the connector cannot tell, say so. Do not post, react or send anything.
```

Last verified: not yet

---

## Step 6 · Gmail

**Why connect it:** Lets Claude find information in your email.

**What Claude can access:** Your mailbox. Do not ask Claude to send, reply, forward or share anything unless you intend to.

**Steps**

1. In the connectors list, find **Gmail** and select the option to connect it. (verify on first run)
2. Sign in with your company Google account. (verify on first run)
3. Approve the access request. (verify on first run)

**What you should see:** Gmail shown as connected in the connectors list.

!!! note "Screenshot needed"
    `assets/screenshots/gmail/01-connected.png`: The connectors list with Gmail shown as connected.

**Verification prompt** (read-only)

```
Using Gmail, read-only: tell me how many unread messages are in my inbox. Do not quote any subjects, senders or content. Do not send, label or delete anything.
```

Last verified: not yet

---

## Step 7 · Google Calendar

**Why connect it:** Lets Claude check your schedule when planning work.

**What Claude can access:** Your calendar events. Do not ask Claude to create, change or share events unless you intend to.

**Steps**

1. In the connectors list, find **Google Calendar** and select the option to connect it. (verify on first run)
2. Sign in with your company Google account. (verify on first run)
3. Approve the access request. (verify on first run)

**What you should see:** Google Calendar shown as connected in the connectors list.

!!! note "Screenshot needed"
    `assets/screenshots/calendar/01-connected.png`: The connectors list with Google Calendar shown as connected.

**Verification prompt** (read-only)

```
Using Google Calendar, read-only: tell me how many events I have today. Do not list titles or attendees. Do not create or change anything.
```

Last verified: not yet

---

## Step 8 · Team skills

**Why connect it:** Skills are our shared, reviewed recipes for Figma work, so you start from what already works.

**What Claude can access:** Skills are instructions Claude follows. They can only do what your connected tools allow, and each skill declares a safety level (see [09 · AI & skills governance](09-governance.md)).

**Steps**

1. Open the `Skills/` folder in Google Drive. It is the single source of truth for the skills library, and the [Skills library](registry/skills-library.md) page lists what is in it.
2. Pick skills marked **Team-approved**. Do not use **Experimental** skills on shared production files.
3. Install each skill using the install note in its own description. (verify on first run)
4. Restart Claude Desktop if the skill does not appear. (verify on first run)

**What you should see:** The installed skills listed in Claude Desktop. (verify on first run)

!!! note "Screenshot needed"
    `assets/screenshots/team-skills/01-skills-folder.png`: The Drive `Skills/` folder showing the Tier column.

!!! note "Screenshot needed"
    `assets/screenshots/team-skills/02-installed.png`: Claude Desktop showing an installed skill.

**Verification prompt** (read-only)

```
List the skills you can currently use. Show only the name and a one-line description for each. Do not run any of them.
```

Last verified: not yet

---

## Verify everything

Run this once all the connectors you want are in place. It only reads and reports. It does not create, change, send or post anything.

```
Check each tool I have connected by doing ONE harmless read-only action, then report in a table with columns: Tool, What you did, Result (OK / Failed / Not connected).
Rules: read only; do not create, edit, send, post or share anything; do not quote email subjects, senders, calendar titles or message content.
- Figma: open <paste your practice file link>; give the file name and its page names.
- Google Drive: give the titles of up to 3 recently modified files in <paste the wiki or Skills folder name>.
- Atlassian: say how many Jira issues are assigned to me (a number only).
- Slack (read-only): say how many channels you can see (a number only).
- Gmail: say how many unread messages are in my inbox (a number only).
- Google Calendar: say how many events I have today (a number only).
- Skills: list the names of the skills you can use.
Skip any tool I have not connected and mark it Not connected.
```

**What good looks like:** a table with one row per connected tool, each marked **OK**, with real names or numbers (not guesses). Tools you did not connect show **Not connected**. Any **Failed** row means that connector needs another look: see the table below.

!!! note "Screenshot needed"
    `assets/screenshots/verification/01-result.png`: the combined verification result table (blur any names you don't want shared).

Last verified: not yet

---

## Troubleshooting

| What you see | What it means | Fix |
|---|---|---|
| "Not authorised" or a permission error | Your account lacks access, or the approval expired | Disconnect and reconnect the connector with your company account. If it persists, check your access in the tool itself |
| Can't see the design library | Your Figma seat or team access doesn't include the library, or the wrong team is selected | Ask the library owner for access, then reconnect and pick the right team. (verify on first run) |
| Wrong workspace or account | You signed in with a personal or other organisation's account | Disconnect the connector, sign out of that account in your browser, then reconnect with your company account |
| Connector appears but returns nothing | It is connected, but nothing matched, or your account can't see what you asked for | Retry with a specific file link or folder name. Check you can open the same thing in the tool directly |
| Admin approval required | IT must allow the connector for your organisation | Note it in your checklist, request approval from IT, and carry on with the other connectors |
| Connector disappears after a restart | The sign-in expired, or a policy removed it | Reconnect it. If it keeps happening, tell IT Ops |

<!-- TODO: add "Stuck?" contact box (Aris Neos, Fredrik Berg) with Slack links -->

---

## Next steps

- [01 · How agents work](01-how-agents-work.md): the mental model and how to choose the right tool.
- [02 · Prompting & context](02-prompting-and-context.md): how to write requests that get good results.

---

### Changelog
| Date | Change | By |
|---|---|---|
| 2026-10-08 | Initial draft | |
