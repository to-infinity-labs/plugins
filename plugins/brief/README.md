# brief

Two Claude Code skills that work well alone and better together.

- **`/decide`** — a decision brief: TL;DR, two or three options tagged by reversibility and size, pros and cons, and **one** recommendation. Doing nothing is always considered; hacks and workarounds are never offered as options.
- **`/tldr`** — says the last answer again, short and in plain words. No jargon, but every number, name and caveat that matters stays. Takes a length: `/tldr 3`, `/tldr one line`.

Run `/decide`, then `/tldr` to get just the call and why it won.

## Install

```
/plugin marketplace add to-infinity-labs/plugins
/plugin install brief@to-infinity-labs
```

Installed as a plugin, the commands are `/brief:decide` and `/brief:tldr`. To use the bare `/decide` and `/tldr`, copy the folders instead:

```
git clone https://github.com/to-infinity-labs/plugins til-plugins
cp -r til-plugins/plugins/brief/skills/decide til-plugins/plugins/brief/skills/tldr ~/.claude/skills/
```
