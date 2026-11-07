# OpenFlow

A way of working with a Claude Code agent in a repository, written as one guide the agent follows:
[`guide/BOOTSTRAP.md`](guide/BOOTSTRAP.md).

The agent in each repository is its **Master**. It keeps the project's state, decisions and history in plain files
under git, so any new session can pick up where the last one stopped without reading old conversations. You stay the
one who decides: the Master asks about facts only you know, decides small judgment calls itself and says what it chose,
and leaves anything that cannot be undone, such as money or a message to a client, for you to order.

## What it gives you

- **A session that starts in the right place.** Every session reads `MASTER.md`, then `system/STATE.md`, then its
  messages, and says in one line where things stand before it acts.
- **One place for each kind of fact.** What is happening now, what is next, stable facts, core decisions and their
  reasons, and an append-only history each have their own file, so they cannot drift apart.
- **Facts you can trust.** Something is written as fact only once it was seen in a file or a command's output, or you
  said it. What only your word supports is tagged with the date you said it.
- **Subagents with limits.** A subagent gets a written brief, a report folder and a cap on how many run at once, and
  its report is checked before anything relies on it.
- **Secrets and client material kept out of git**, and documents with legal value never deleted.
- **Masters that message each other** through folders in each other's repositories, when you run several projects on
  one machine.

## Set up a repository

1. Copy [`guide/BOOTSTRAP.md`](guide/BOOTSTRAP.md) into the root of your repository as `BOOTSTRAP.md`.
2. Open Claude Code there and ask it to set the repository up with `BOOTSTRAP.md`.
3. Answer its three questions: the project's name, whether it may touch live systems, and whether the repository may
   go public one day.

The agent creates `MASTER.md`, `CLAUDE.md` and a `system/` folder, moves what the project already has into place,
deletes `BOOTSTRAP.md` and commits. From then on, every session starts from `MASTER.md`.

Part 1 of the guide is the setup. Part 2 is the rules, which the agent copies word for word into `MASTER.md`, so a
project can be read without the guide. A project adds its own rules on top, as P1, P2 and so on, and a project rule may
be stricter than a guide rule.

## Versions

The guide's version is in its second line, as `Vx.y.z`: x for a rewrite, y for a rule or setup change, z for wording
only. Each project's `MASTER.md` carries a `Guide version` line, which is how you tell which rules it is on.

To move a project to a newer version, give its Master the new `guide/BOOTSTRAP.md` and ask it to apply the rules that
changed to `MASTER.md` word for word and update its `Guide version` line. Rule numbers never move, because projects
cite them: new rules are added at the end.

The guide names `openflow master` as the agent that keeps it. That is the Master of this repository. If you keep your
own copy of the guide, that role is yours.

## License

[CC0 1.0](LICENSE): the guide is in the public domain. Copy it, change it and paste its rules into your own `MASTER.md`
without any notice.
