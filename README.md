![Tedate. A prompt isn't a product.](assets/tedate-banner-1200x630.png)

**English** · [简体中文](README.zh-CN.md) · [日本語](README.ja.md)

# Tedate

A product-judgment skill for Claude Code and Codex that helps you decide what to build, what to change, and whether the result works.

- **Choose the next move.** Turn an idea, a feature request, or “something feels wrong” into a clear recommendation.
- **Give the work direction.** Define a focused task for design or engineering, carrying your goal and the decisions you've already made.
- **Judge the result.** Check whether the work solved the original problem, what still needs attention, and when to stop.

Your agent can build the feature. You still have to decide whether it belongs, whether the experience works, and when to stop. You can ask your agent for any of this yourself; Tedate writes it down as a default way of working when you use it.

**You own the product. Your agent builds it.**

*Tedate takes its name from 手立て, Japanese for a way or means of doing something.*

[Install](#install) · [See it in use](docs/examples.md) · [Working with other skills](docs/working-with-other-skills.md)

Preview · MIT licensed · [Good to know](#good-to-know)

## When another iteration isn't helping

You ask for a redesign. The page gets cleaner, but still doesn't help someone do what they came to do.

You add another feature. It works, but you are less sure what the product is for.

Your agent reports that every test passes. You still don't know whether the original problem is solved.

These are the moments Tedate is written for. It helps make the judgment explicit: what matters here, what should change, what should stay, and what evidence would be enough.

Sometimes the recommendation is to build. Sometimes it is to investigate one uncertainty, reduce the scope, or leave things alone.

## A checkbox isn't a next step

In one of the author's runs, a family health-information page felt awkward to use at medical appointments.

Reading the code, the agent found a likely gap: the page let someone tick **“I know the next step,” but none of the ticks recorded what that step was.** The ticks also disappeared when the visit view closed.

The proposed next move changed. Before redesigning the page, replay one recent difficult appointment and find the moment it stopped helping: preparing questions, recording answers, or knowing what to do afterwards.

That is the kind of judgment Tedate is intended to support: finding a more useful problem to work on before asking for another version.

[Read the fuller account and an illustrative answer](docs/examples.md)

## Bring one decision you're stuck on

- **Too much to build:** “Which of these ideas deserves attention now?”
- **Another unsatisfying redesign:** “I've tried two versions. What is still wrong?”
- **A choice between directions:** “Which approach better serves what we're trying to do?”
- **An agent says it's done:** “What shows that the original problem is actually solved?”

Expect a recommendation and a reason tied to your situation. Anything beyond a small question also says what was not checked and who does what next, and a larger decision states what result would change the recommendation.

You don't need a finished brief. A real example of where things stop working is a useful place to start.

## Keep the purpose through the build

Software has a principle: don't repeat yourself. Skills are the same. Good specialist skills already exist for interviewing, design and engineering, and Tedate would rather work with them than rebuild them. It can handle a decision on its own, and it is designed to hand off to a specialist when a question needs deeper work.

Use an interview skill to explore the idea, a design skill to shape the experience, and an engineering skill to build it. Tedate helps carry the product goal and accepted decisions through those hand-offs, then checks the result against the original intent.

![Tedate carries your goal and accepted decisions into one focused task for a specialist skill (interview, design or engineering), then checks the result against your original goal: if solved, you decide what happens next; if not, Tedate names what is missing and the loop repeats.](assets/tedate-handoff.png)

For example (illustrative), “make this page better” might become a focused design task: give the recipe title a clear visual priority and use the existing card spacing. The review then returns to those same issues on the same page, alongside whether the overall result works.

Small questions can stay small. Other skills are optional; without them, Tedate can still give a recommendation and an actionable task.

For work across sessions, Tedate keeps accepted decisions in a short record in your project, written only with your OK. It does not give your agent memory of its own, and another skill may not follow a hand-off.

When installed skills pull your agent different ways, say one insists on tests first and another says ship now and test later, Tedate proposes how to handle it from the decisions you have accepted and carries that into the hand-off task. Where you haven't decided, it recommends an approach for you to accept. If you switch skills, the direction you already confirmed is written into the hand-off task.

[How the hand-offs work](docs/working-with-other-skills.md) · [What the answers look like](docs/outputs.md)

## Install

### Claude Code (plugin)

```bash
claude plugin marketplace add fengyu20/tedate
claude plugin install tedate@tedate
```

In a new session (a plugin's skills carry the plugin name as a prefix):

```text
/tedate:tedate This page looks off, but I can't say why.
```

It may also trigger when your request matches its description.

### Or copy the skill folder (Claude Code or Codex)

Clone this repository (or download it as a zip), then copy `skills/tedate` into your skills directory. The folder must stay named `tedate`.

```bash
git clone https://github.com/fengyu20/tedate.git
cd tedate
```

Claude Code:

```bash
mkdir -p ~/.claude/skills
cp -R skills/tedate ~/.claude/skills/
```

Then `/tedate This page looks off, but I can't say why.`

Codex:

```bash
mkdir -p ~/.agents/skills
cp -R skills/tedate ~/.agents/skills/
```

Then `$tedate This page looks off, but I can't say why.` If it does not appear, restart Codex.

Tedate opens by naming its mode: `advise`, `delegate` or `execute`. That is a sign it was used; the useful check is whether its advice helps you make a real decision.

To update the plugin, run `claude plugin update tedate@tedate`; to uninstall it, `claude plugin uninstall tedate@tedate`. If you copied the folder, pull the repository and copy `skills/tedate` again; to uninstall, remove the `tedate` folder from your skills directory.

## Good to know

- **Its judgment can be wrong.** Asking for sources and dates does not make the underlying facts correct. You make the call.
- **Hand-offs depend on your setup.** Other skills are optional, and whether one follows a hand-off depends on that skill and your environment. [Why Tedate hands off](#keep-the-purpose-through-the-build). Tedate overlaps with existing product and design skills such as [Impeccable](https://github.com/pbakaus/impeccable), [gstack](https://github.com/garrytan/gstack) and PM skill packs. Tedate only hands off to skills you have installed, and you decide whether to install one.
- **What it reads and writes.** It reads your project files, git history and any analytics you point it to, and may ask your agent to look up public sources. It writes a decision record only with your OK. It ships no scripts and sends no data anywhere itself; sending your idea to a third-party service needs your yes.
- **Scope is product judgment.** It does not manage releases, version numbers or merge conflicts, run channel-specific marketing tactics, or produce PRDs or roadmaps.
- **You stay in charge of consequential actions.** It is instructed not to spend money, publish or deploy without your explicit yes, and never to contact people for you. These are prompt rules, not technical safeguards.

## Background

I build [PYOKO](https://pyoko.jp/?utm_source=github&utm_campaign=tedate-readme), an unofficial guide to the Grutto Pass, a museum pass for Tokyo, mostly together with coding agents. But getting something built didn't settle whether it was the right thing to build. When I let agents change a page on their own, it sometimes became harder to use. I could tell something was wrong, but there was a gap between that feeling and knowing what to change. A task was reported done while the problem that started it was still there. And once the site was live, few people came, which raised a different question: who to reach first, and how to tell whether it worked.

So I started writing down how I wanted those calls made: who the page is for, what evidence will count as done, which decisions we had already made and should keep, and whether the result solved the original problem. Most rules came from a specific run that went wrong, on PYOKO and on a few side projects. Over time, I collected those working notes into Tedate. It is meant to help close that gap: to turn “this feels wrong” into a clearer understanding of the problem and a concrete next step, while you still make the call.

Questions or feedback? [Open an issue](https://github.com/fengyu20/tedate/issues).
