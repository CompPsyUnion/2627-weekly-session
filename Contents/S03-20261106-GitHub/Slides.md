---
marp: true
theme: cpu
paginate: true
html: true
---

<style>
/* deck preference: side-pinned images vertically centred and never capped */
section.side img {
  top: 50%;
  transform: translateY(-50%);
  max-width: none;
  max-height: none;
}
</style>

<!-- _class: lead -->
<!-- Cover: CPU weekly session 03, presenter Siyuan He (Robert), 6 November 2026 -->

# GitHub Beyond the Code

## From a Fork to Your First Merged PR

Siyuan He (Robert)

Computer Psycho Union · 6 November 2026

### WEEKLY 03

#### CPU 2026/27

---

<!-- _class: agenda -->
<!-- Agenda: five items, first row auto-highlighted -->

## What we will cover

1. Record a problem *Issues*
2. Fork & branch *copy it home, one change per branch*
3. Give it back *Pull Request — today's hero*
4. Robot checks *Actions*
5. Ship it as a website *Pages*

---

<!-- Regular content page: two columns (1/3 + 2/3), image below -->

<style scoped>
/* force 1/3 + 2/3 and top-align both columns (theme centres vertically) */
div.columns {
  align-items: flex-start;
}
div.columns > div.column {
  flex: 0 0 30%;
}
div.columns > div.column:last-child {
  flex: 2;
}
</style>

## 01 · More than code storage

<div class="columns">
<div class="column">

### YOUR PROFILE

- Avatar
- Pinned repos
- Green squares

</div>
<div class="column">

### STRANGERS, ONE CODEBASE

- **@CompPsyUnion/2627-weekly-session**
- **@unnc-aim/26RC_R2_ws**
- **@microsoft/vscode**

</div>
</div>

![w:1000](assets/repo-overview.png)

---

<!-- Regular content page: landscape placeholder below the text -->

## 02 · Today's question

- **You don't know the repo owner** — how do you safely hand your change back?
- No direct push, no trust — and yet the world ships this way every day

<!-- ![w:960](assets/fork-button.png) -->
![w:1100](assets/playground-overview.png)

---

<!-- _class: side -->

![w:570](assets/typo-drowned.png)

## 03 · Bug report, drowned

### WHAT HAPPENED

- You spotted a typo in a project README
- You reported it in the group chat
- **DROWNED by other messages.**

<br/>

### THE QUESTION

Where should problem reports / feature requests live, so they don't get lost?

---

<!-- _class: side -->
<!-- Screenshot focus: right sidebar (labels/assignees/milestone) — image LEFT -->

![w:560](assets/issues-list.png)

## 04 · Issues

### A SHARED TODO

A typo in the README / A feature wish
Too easy to lose in a chat group.

<br/>

### NUMBERED & PUBLIC

- A number
- label, assignee, milestone

---

<!-- _class: side -->

![w:540](assets/new-issue.png)

## 05 · Create an Issue

### YOUR TURN

Open a new issue on the playground repo — propose a **profile addition** with a clear title & a short description.

<br/>

### REMEMBER THE NUMBER

`Fixes #N` later links your PR to this issue.

#### #N

---

<!-- Regular content page: screenshot focus is the error banner at the top — image below -->

## 06 · Problem: modification denied

### WHAT HAPPENED

You tried to add a file directly to our repo — `permission denied`.
Of course: the repository is not yours, and that is a feature, not a bug.

### THE QUESTION

How do you get your own copy to work on?

![w:820](assets/push-denied.png)

#### DENIED

---

<!-- _class: side -->
<!-- Screenshot focus: the Fork button, top-right corner — image LEFT -->

<style scoped>
section.side {
  padding-left: 620px;
}
section.side img {
  right: auto;
  left: 0;
}
section.side h4 {
  left: auto;
  right: 84px;
}
</style>

![w:580](assets/fork-button.png)

## 07 · Fork: copy it home

### YOUR OWN COPY

- Duplicates the whole repo
- Under your account
- Break it freely
- Upstream stays untouched.

#### FORK

---

<!-- Regular content page: screenshot focus is the Add file bar at the top — image below -->

## 08 · Branch first

### TAKE THIS AS A RULE FIRST

Create a `docs/...` branch before adding any files — `docs/yourusername-add-profile`.

![w:960](assets/create-branch.png)

---

<!-- Regular content page: four-step screenshot strip, equal height -->

<style scoped>
/* four workflow screenshots in one equal-height row */
.shotrow {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  gap: 14px;
  margin-top: 26px;
  /* lift the strip above the theme's dashed blueprint guides */
  position: relative;
  z-index: 1;
}
.shotrow p {
  margin: 0;
}
.shotrow img {
  height: 270px;
  width: auto;
}
</style>

## 09 · Add your profile on the new branch

### HANDS-ON

**Go to your new branch's homepage** → `profiles/` → **Add file → Create new file** → `<your-username>.md` → commit.

<div class="shotrow">

![Click your new branch in the branch list](assets/branch-list-page.png)

![Your branch's homepage](assets/branch-page.png)

![Create new file under profiles/](assets/create-new-file.png)

![Commit new file on the branch](assets/commit-new-file.png)

</div>

---

<!-- Regular content page: screenshot focus is the base/compare dropdowns at the top — image below -->

## 10 · Pull Request: the letter

### COMPARE & PULL REQUEST

GitHub notices your branch is ahead and offers to propose the merge.

Note: Branches, PR Title, Body (use `Closing keywords`)

![w:760](assets/compare-pr.png)

#### PR

---

<!-- _class: side -->
<!-- Screenshot focus: the PR tab bar, top of the page — image right -->

## 11 · Anatomy of a pull request

### NOT A COMMAND

A PR is a request for review.

<br/>

### TABS

- **Conversation** — the whole story
- **Commits** — the saves
- **Checks** — **Actions** done by bots.
- **Files changed** — line-by-line diff

![w:560](assets/pr-tabs.png)

---

<!-- _class: side -->

![w:560](assets/wall-of-lines.png)

## 12 · Problem: a wall of lines

### WHAT HAPPENED

Your PR arrives — hundreds of changed lines from a stranger. The maintainer has thirty more like it today.

<br/>

### THE QUESTION

How can anyone trust code they did not write?

---

<!-- _class: side -->
<!-- Screenshot focus: review buttons, top-right of the PR page — image LEFT -->

<style scoped>
section.side {
  padding-left: 620px;
}
section.side img {
  right: auto;
  left: 0;
}
section.side h4 {
  left: auto;
  right: 84px;
}
</style>

![w:570](assets/review-buttons.png)

## 13 · Review

### ON STAGE

Live demo: pick one PR, comment on a line, **Approve**.

<br/>

### THE CULTURE

Review the code, not the person; describe what and why.

#### RESPECT

---

<!-- _class: side -->

![w:540](assets/merge-dropdown.png)

## 14 · Merge: three shapes of history

### PICK ONE

- **Merge commit** — keep everything
- **Squash** — compress to one
- **Rebase** — replay in a line.

<br/>

### IN THIS REPO

Nobody clicks — the robot squash-merges every PR that passes the checks.

---

<!-- _class: side -->

![w:540](assets/closing-keyword.png)

## 15 · Fixes #N — the loop closes

### THE CLIMAX

A PR whose commit message says `Fixes #N` closes issue `#N` the moment it merges.

<br/>

### FULL TRACE

Problem → issue → fix → PR → merge → closed. That is open source.

#### CLOSED

---

<!-- Regular content page: two scenario columns + takeaway below, image at the bottom -->

<style scoped>
/* two equal scenario columns, top-aligned (theme centres vertically) */
div.columns {
  align-items: flex-start;
}
</style>

## 16 · A NEW Branch, Why?

<div class="columns">
<div class="column">

### YOUR OWN PROJECT

Branch off `main`, build the change, open a PR into **your own `main`**.

</div>
<div class="column">

### CONTRIBUTE UPSTREAM

Branch in your fork, open a PR into **upstream's `main`** or any recommended

</div>
</div>

### EITHER WAY, ALL ROADS END IN `main`

You seldom commit straight onto your own `main`

![w:660](assets/tangled-main.png)

---

<!-- Regular content page: screenshot focus is the checks banner at the top — image below -->

## 17 · The mystery stamp?

### WHAT HAPPENED

You open the PR page — a spinner spins, then a green tick or a red cross appears. Nobody clicked anything; the merge is blocked.

- Who — or what — is checking the code?

![w:960](assets/mystery-stamp.png)

---

<!-- _class: side -->

![w:540](assets/actions-log.png)

## 18 · Actions: bot colleague

### CHECKS EXPLAINED

Every green tick is a workflow we wrote: one file, your username, content rules.

<br/>

### WATCH IT WORK

Open the Actions tab in your fork — step-by-step logs.

#### CI

---

<!-- _class: side -->

![w:560](assets/checks.png)

## 19 · Red X - a safety net

### CAUGHT IN THE ACT

Wrong filename, someone else's name, an extra file — the robot blocks the merge.

<br/>

### NOT PUNISHMENT

The robot stops problems before they reach main.

#### GUARD

---

<!-- _class: side -->

![w:550](assets/share-problem.png)

## 20 · Site written, host it?

### WHAT HAPPENED

The page works on your machine. Sharing it means sending a zip — or worse, "just clone my repo".

<br/>

### THE QUESTION

How does a repository become a plain link?

#### SHARE

---

<!-- Regular content page: screenshot focus is the "site is live" banner at the top — image below -->

## 21 · Pages: repo becomes a website

### THE ROBOT MOVED IN WITH YOU

Your fork carries the same workflows — GitHub just parks them. Open your fork's **Actions** tab and click **Allow** (*I understand my workflows, go ahead and enable them*).

Press **Sync fork** — upstream's `main` lands on yours, CI wakes up by itself and your copy of the site deploys.

![w:860](assets/actions-allow.png)

---

<!-- _class: side -->

![w:540](assets/roster.png)

## 22 · The roster page

### ONE CARD PER PROFILE

Avatars straight from `github.com/<username>.png` — rebuilt by CI on every merge.

<br/>

### VISIT EACH OTHER

Your roster now lives at `username.github.io/github-playground` — post the link in the group.

---

<!-- _class: yellow -->
<!-- Closing page -->

## THANK YOU

### Q&A

#### Your Green Square Starts Today

Siyuan He (Robert) · Computer Psycho Union · 6 November 2026
