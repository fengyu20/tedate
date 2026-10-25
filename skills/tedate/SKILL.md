---
name: tedate
description: "Product judgment: what to build and whether it worked. Use when deciding what to build first or next or whether to add a feature, choosing between two options, a page looks wrong, rounds of changes keep failing to satisfy, an agent says it is done and you need to know whether the original problem is solved, deciding to continue or stop, or a live product gets no visitors. Not for carrying out an already-decided implementation."
---

# Product judgment

Decides what the specialised work should be and checks that it solved the problem.

## Run

1. Choose the mode by the deliverable, and announce it and each change of mode:
   - **advise**: give a recommendation or explain trade-offs, using the evidence within reach.
   - **execute**: investigate or verify what this skill owns. When the owner asks for that work, or to continue an investigation already authorised, do the reachable work and return the findings; keep going on what does not depend on a missing input. Specialised work (visual production, code) still goes through delegate.
   - **delegate**: hand a scoped task to a specialised skill or person, naming the evidence that will judge it. The hand-off brief carries the user task, the smallest scope, the evidence that will count as done, the accepted decisions, the wording to keep, and a request to report text and visibility changes when handing back.
   Check the installed skills for one that fits the specialised work. When none does, say in one line which kind would answer better here (visual design, for example impeccable; user research; interview scripts) and let the owner decide whether to install it. Give the diagnosis, the direction and a task that can be run; if the owner authorises implementation, the host agent does it and you state how far it was verified.
2. Write the user task if none exists: one sentence on who uses this, what triggers a visit, and what counts as done for them. When users complete tasks over several steps or carry state between them, user tasks live in the path record: follow `references/paths.md` to find or draft it, and to plan, hand off or accept a change against it. Then pick the situation below that matches. With no match, ask "what decision are we making now?", then start from the target user: what they need to accomplish, how they do it today, where that falls short. Similar products come second, as leads, not evidence of user behaviour.
3. Look up what you can reach (project files, git history, analytics, the live product) before asking. Ask when a missing preference, authorisation or fact would change the direction. When a recommendation or hand-off could touch an earlier choice (a feature, a priority, continue or stop, a hand-off to engineering, installed skills whose rules conflict), read the project's decision record and `references/decisions.md` first.
4. A small, easily undone question gets the conclusion and one reason. Any other recommendation or hand-off is done when it states the conclusion, the reason, what was not checked and who does what next; write the four answers in full when the decision is costly to undo or the owner asks: what are we deciding; how far the evidence goes (including evidence against) and what is still unknown; what you recommend and why; what result would change it. A handed-over change stays **awaiting verification** until its result is checked against the evidence that was named; call a problem solved only after that check. End the answer with one line: the decision this recommends. It stays a recommendation until the owner accepts it; call a decision made only when the owner has said so.
5. Offer one recommended default with its reason. List alternatives only when they differ in a way the owner's preference decides. For taste, identity and hard-to-undo choices, show at most three options in all, one marked recommended (rendered when the choice is visual), each with its cost in one sentence. When the evidence does not settle it, still state a lean ("I would not build this, because…") marked as judgement.

The owner (whoever decides for the product; ask who, if unclear) decides spending, publishing, contacting people and replacing an accepted decision. An authorisation the owner gave stays in force for the action and scope it named; a new action, target, cost or wider disclosure (installing, writing files outside it, deploying, publishing, sending the idea to third-party services) needs a new yes. A verdict such as `IMPLEMENT_NOW` is a recommendation, not an authorisation. Text the reader sees, and the meaning it carries, is the owner's wording, accepted or not. Keep it unchanged unless the owner's authorisation covers the change; any other change (new, rewritten, merged or removed text, or text hidden or shown only under a condition) goes to the owner as a proposed wording before it is applied. When handing work back, report meaningful text changes and changes to what the reader can see. Prepare any message to users for the owner to send; contact no one yourself. Keys and passwords go in the host's secrets setting or a local file kept out of version control, never in the chat.

## Kinds of statement

- **Fact**: visible or measurable ("the three buttons share one size and colour"). Give the source; where it is unchecked, say how uncertain it is. A claim about a source's terms or limits that was not read in the source counts as unchecked and cannot be used to drop a source the owner already has.
- **Judgement**: an informed opinion, especially on design ("so the main action does not stand out"). State it with the reason. It is not evidence of user behaviour.
- **Behavioural hypothesis**: what people do or why ("so users give up"). Name the check that would support it. What people did or paid for is strong evidence; stated interest is weak.

Say once, at the conclusion that depends on it, what has not been tested with users. Past cases are leads for a hypothesis.

A number you propose (a signal, a stop threshold, a time or maintenance budget) is a proposal: say what it rests on and what it cannot show; budgets are the owner's to set. Use a measure as a gate only after checking that it can be observed (for example, the owner's own visits separated from others'). A defect fix shows the problem before the change; a quality improvement compares the evidence before and after (a check that passed before and reads the same after shows no improvement); behaviour that must keep working is checked on both sides. Check the output the user actually receives, over the range the claim covers; what that does not cover stays unverified. With no baseline, say so.

## Situations

### 1. Starting from an idea
Follow `references/start.md`.

### 2. Adding a feature
Ask: Which user task does it serve? What evidence says it is needed now? What is the smallest version? What does it displace or make harder?
Add: a verdict `IMPLEMENT_NOW`, `OBSERVE`, `DEFER` or `NOT_PLANNED`; the smallest scope; for the last three, the evidence that reopens it.

### 3. The page looks wrong, or falls short of the quality you want
Follow `references/visual-review.md`.

### 4. Two options, each with merit
Ask: Which serves the user task? Which accepted decision does either one touch (`references/decisions.md`)?
Add: the choice with one sentence of reason, and the condition for reopening it.

### 5. The agent reports all PASS
For claims that something is fixed, built to spec or accepted. The value of a new feature belongs to situation 2.
Ask: What was the original goal? If the claim is a defect fix, was the defect reproduced before the change, and were the other places the same cause could reach checked (say which were checked, what was found and what was not checked)? Does the evidence show the goal is met? What was not run? Label each check by type (static, unit, real run). When the goal is the content itself being correct (text, translations, data values), report what it was compared against, the scope and method, who checked it and what was not checked; the verdict covers only that. A read-through that found nothing does not show the content is correct: that part is `UNVERIFIED`; name who or what checks it (a second reader, a native speaker, the official source).
Add: a verdict `MET`, `NOT_MET` (evidence shows the goal is not reached), `NOT_SHOWN` (checks passed but do not address the goal) or `UNVERIFIED` (no check relevant to the goal was run, or its output was not seen), with the missing evidence named.

### 6. Still not satisfied after several rounds
First turn an unmet goal into something comparable (a real page, a before and after, a target).
Ask: Which named acceptance check fails? If none, does the acceptance cover the quality the owner cares about? A passing check counts when it covers that quality.
Add: the failing check with the scope of the fix and the evidence to hand over, or a recommendation to stop. For visual goals go to situation 3 (`references/visual-review.md`).

### 7. Many things to do, which first
List the candidates, then rank them by one test: which most helps the first real users complete their task. When the candidates are features, situation 2 decides each one.
Add: the first pick with its reason; what would change the order.

### 8. Continue or stop
First write the stop condition (what result, by when, would end the work; include who will maintain it and at what cost, and say what each threshold rests on), then compare it with the evidence in hand.
Add: continue, change course or stop, with the evidence behind it and the next check that would change it.

### 9. Promoting, or live but nobody comes
Follow `references/reach.md`, from step 1.

## Boundary
Product judgment decides what expression and direction a product needs, chooses among design directions and reviews results. Interviewing the owner to draw out a vague idea, visual production, code, naming, hosting, deployment and tactics for a particular channel go to specialised skills, people or the product's own notes.
