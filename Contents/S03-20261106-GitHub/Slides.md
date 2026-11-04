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

<!-- _class: side -->

![w:540](assets/vscode-repo.svg)

## 01 · More than code storage

### YOUR PROFILE

- Avatar
- Pinned repos
- Green squares

<br/>

### STRANGERS, ONE CODEBASE

**2627-weekly-session** | **microsoft/vscode**

---

<!-- Regular content page: landscape placeholder below the text -->

## 02 · Today's question

- **You don't know the repo owner** — how do you safely hand your change back?
- No direct push, no trust — and yet the world ships this way every day

![w:760](assets/fork.svg)

---

<!-- _class: side -->

![w:540](assets/issues-list.svg)

## 03 · Issues

### A SHARED TODO

A typo in the README, a feature wish — too small for a PR, too easy to lose in a chat group.

<br/>

### NUMBERED & PUBLIC

- A number
- label, assignee, milestone

---

<!-- _class: side -->

![w:540](assets/new-issue.svg)

## 04 · Create an Issue

### YOUR TURN

Open a new issue on the playground repo — propose an improvement, two or three lines, a clear title.

<br/>

### REMEMBER THE NUMBER

`Fixes #N` later links your PR to this issue.

#### #N

---

<!-- _class: side -->

![w:540](assets/fork.svg)

## 05 · Fork: copy it home

### NOT YOUR REPO

You cannot push to someone else's repository — that is a feature, not a bug.

<br/>

### YOUR OWN COPY

Fork duplicates the whole repo under your account; break it freely, upstream stays untouched.

#### FORK

---

<!-- _class: side -->

![w:540](assets/new-file.svg)

## 06 · Branch first, then edit

### WHY NOT MAIN?

Main stays in sync with upstream; one change per branch — `docs/add-<your-username>`.

<br/>

### HANDS-ON

`profiles/` → **Add file → Create new file** → `<your-username>.md` → commit on a new branch.

---

<!-- _class: side -->

![w:540](assets/compare.svg)

## 07 · Pull Request: the letter

### COMPARE & PULL REQUEST

GitHub notices your branch is ahead and offers to propose the merge.

<br/>

### READ THE DIRECTION

base ← upstream `main` · compare ← your fork's branch.

#### PR

---

<!-- _class: side -->

![w:540](assets/pr-anatomy.svg)

## 08 · Anatomy of a pull request

### TABS

**Conversation** — the whole story
**Commits** — the saves
**Files changed** — line-by-line diff
**Checks** — **Actions** done by bots.

<br/>

### NOT A COMMAND

A PR is a request for review.

---

<!-- _class: side -->

![w:540](assets/review.svg)

## 09 · Review: three verdicts

### ON STAGE

Live demo: pick one PR, comment on a line, **Approve**.

<br/>

### THE CULTURE

Review the code, not the person; describe what and why.

#### RESPECT

---

<!-- _class: side -->

![w:540](assets/merge-dropdown.svg)

## 10 · Merge: three shapes of history

### PICK ONE

**Merge commit** — keep everything · **Squash** — compress to one · **Rebase** — replay in a line.

<br/>

### IN THIS REPO

Nobody clicks — the robot squash-merges every PR that passes the checks.

---

<!-- _class: side -->

![w:540](assets/checks.svg)

## 11 · Fixes #N — the loop closes

### THE CLIMAX

A PR whose description says `Fixes #N` closes issue #N the moment it merges.

<br/>

### FULL TRACE

Problem → issue → fix → PR → merge → closed. That is open source.

#### CLOSED

---

<!-- _class: side -->

![w:540](assets/actions-run.svg)

## 12 · Actions: the robot colleague

### CHECKS EXPLAINED

Every green tick is a workflow we wrote: one file, your username, content rules.

<br/>

### WATCH IT WORK

Open the Actions tab in your fork — step-by-step logs.

#### CI

---

<!-- _class: side -->

![w:540](assets/checks.svg)

## 13 · Red cross is a safety net

### CAUGHT IN THE ACT

Wrong filename, someone else's name, an extra file — the robot blocks the merge.

<br/>

### NOT PUNISHMENT

The robot stops problems before they reach main.

#### GUARD

---

<!-- _class: side -->

![w:540](assets/pages-settings.svg)

## 14 · Pages: repo becomes a website

### FREE HOSTING

Settings → Pages → Deploy from a branch → `main` / `/docs`.

<br/>

### UPSTREAM vs FORK

Upstream deploys automatically via Actions; in your fork, you flip the switch once.

---

<!-- _class: side -->

![w:540](assets/roster.svg)

## 15 · The roster page

### ONE CARD PER PROFILE

Avatars straight from `github.com/<username>.png` — rebuilt by CI on every merge.

<br/>

### VISIT EACH OTHER

Post your `username.github.io/github-playground` link in the group.

---

<!-- Regular content page -->

## 16 · Final exercise: connect the dots

- New branch → edit `docs/` → commit → **PR to your own repo**
- Checks run again → merge → the website updates itself

![w:760](assets/roster.svg)

*Change → robot checks → deploy. You built the whole pipeline.*

---

<!-- _class: yellow -->
<!-- Closing page -->

## THANK YOU

### Q&A

#### Your Green Square Starts Today

Siyuan He (Robert) · Computer Psycho Union · 6 November 2026
