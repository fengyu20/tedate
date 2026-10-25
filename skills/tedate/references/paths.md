# User paths

Read when users complete a task over several steps or carry state between them (saved items, filters, language, coming back later), on one page or across pages.

A **path** is one user task as the owner wants it: the **entries** (direct URL, shared link, search, Back) and the **steps** to the task's done mark. Write the task, not the buttons. Each step has an observable **done mark**, the state it carries on (saved item, language, date), and **how it is checked now**: an automated test (file), a missing assertion (written out), a human judgement with its evidence, or unverified. A step checked by human judgement or left unverified is recorded as it is, not reported as a defect.

## 1. Find or draft the record

Look for `docs/user-paths.md`, an AGENTS.md pointer, or a doc that already lists user tasks with steps. With none, draft in the reply the few paths that cover the main tasks, mark them a proposal, ask the owner to accept or correct, and name the file you would write (default `docs/user-paths.md`). Only after acceptance, write that file with exactly the accepted content. Add the AGENTS.md pointer ("Before a change that touches a user task, read docs/user-paths.md.") only with the owner's yes. When the owner asked for a plan or hand-off, draft only the paths the change touches, mark them unaccepted, and continue to §2 against them.

Per path: its name, its entries, then the table:

| Step | Done mark | State carried on | How it is checked now |
|---|---|---|---|

**Done when** the owner has accepted the paths, or the proposal is in front of them.

## 2. Plan against the record

Name the path and each step the change touches. For a new entry or second surface, state how a user who starts there completes the same task: the same meaning of status and records, and the state it needs (language, saved items, return context). It may hand off to an existing surface instead of copying its features; a presentation the product chose on purpose is not a conflict.

Sort what you find:
- The change alters no done mark, entry or carried state (a footer contact detail, for example): say so in one line and leave the record out. Wording and layout touch a step when they change what the user does next.
- The change misses a done mark: a gap. Fix it within scope or name it. The accepted path stands; do not ask for re-approval.
- New needs or evidence challenge the path: give reasons, effect and options; the owner decides whether to update the record.
- Only facts in the record are stale: correct them with the owner's authorisation.
- Security or data upkeep: say what it protects.

**Done when** every touched step has its done mark planned, or is named as a gap or an owner question.

## 3. Hand off and accept

Per touched step the hand-off gives: the done mark; where it is implemented, and the other readers of that state; the existing test and what it covers; the assertion to add, or the human check. Accept only the touched steps: walk a key task's whole path end to end; check a rule (a status, a storage write) with a unit test. A claim that a check cannot run names the operation tried and its error; a browser missing from PATH does not show that none is installed.

Acceptance labels each touched done mark with a SKILL.md situation 5 verdict, with the blocker.
