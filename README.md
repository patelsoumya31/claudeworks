# claudeworks

## The Arena skill

When Claude keeps giving you bad answers, make 100 versions of it fight to the death. One Claude
Code skill. Free, MIT, no signup, no API key, nothing to connect.

You use it when you are not happy with what Claude gave you. Instead of asking again and again,
`/arena` spins up 100 sub-agents and gives every one of them the exact same task, word for word.
Each one gets a different strategy card: a way of reasoning, a workflow and a strategy, so each one
attacks the task differently. Then they pair off. Each attacks the other's solution, each defends
and revises its own, and a judge scores the match on a written rubric. The loser is out. 100
becomes 50, then 25, 13, 7, 4, 2, 1.

What comes back is the one solution that survived, the attacks it beat on the way, and how many
rounds it took.

**It never touches your files.** Every sub-agent writes inside `.arena/`. The winning answer comes
back to you, and using it is your call.

Original source: [Jakeschincariol/arena-skill](https://github.com/Jakeschincariol/arena-skill).

### Installed here

This repo mirrors the upstream layout and ships the skill two ways:

```
skills/arena/              the canonical copy of the skill (SKILL.md, bracket.py, strategies.json, rubric.md)
.claude/skills/arena/      the same skill, installed project-locally so /arena works in this repo
.claude-plugin/            plugin.json + marketplace.json, so this repo can also be added as a plugin marketplace
tests/test_bracket.py      the upstream test suite for bracket.py
```

Because it's copied into `.claude/skills/`, `/arena` is available directly in this repo without any
extra install step.

### Use it

```
/arena
/arena --quick write the headline for our pricing page
/arena --agents 32 fix the flaky test in tests/test_api.py
/arena --seed 7 plan my launch week, I have 6 hours a day
```

| flag | what it does |
| --- | --- |
| `--agents N` | N competitors. Default 100. |
| `--quick` | 16 competitors. The everyday setting. |
| `--seed S` | Same seed, same cards and same bracket. Default random, and recorded. |
| `--wave W` | Sub-agents per wave. Default 10. Only raise it if you raised Claude Code's limit. |

It needs Claude Code, because it spawns sub-agents with the Agent tool, and Python 3.8 or newer.
Nothing to pip install.

### Tests

```bash
python3 -m unittest discover -s tests -v
```

### Credit

Made by Jake Schincariol, [opusjake.ai](https://opusjake.ai). MIT licensed — take it, change it, ship it.
