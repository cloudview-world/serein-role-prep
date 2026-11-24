# Serein Role Prep

[中文说明](README.zh-CN.md)

An Agent Skill that turns your character material into Markdown you can paste straight into **Serein (栖语)**, the AI companion app.

- **Normal creation**: a card with one block per field (name, gender, content language, tags, intro, opener, persona, worldview), each kept within Serein's limits with a 10% margin.
- **Persona replica**: one compact document that Serein's 人格复刻 reads in a single request instead of splitting your material into dozens of requests.

Your agent can read what Serein cannot: PDF, Word, web pages, screenshots, or just a name. It asks you one question (normal creation, persona replica, or both) and writes the files.

Version **1.0.0** · for Serein **0.1.0** (builds from November 2026) · [MIT License](LICENSE)

## Install

The skill is this whole repository: put it in your agent's skills folder as a folder named `serein-role-prep`. The easiest way is to tell your agent:

> Install the skill from https://github.com/cloudview-world/serein-role-prep

Or do it yourself with git. On Windows, `~` means your user folder (`C:\Users\<you>`).

| Agent | Your skills folder | Install yourself | Checked |
|---|---|---|---|
| Claude Code | `~/.claude/skills/serein-role-prep` | `git clone https://github.com/cloudview-world/serein-role-prep ~/.claude/skills/serein-role-prep` | Installed from GitHub and used |
| Codex | `~/.agents/skills/serein-role-prep` | `git clone https://github.com/cloudview-world/serein-role-prep ~/.agents/skills/serein-role-prep` | Official docs |
| DSH (DeepSeek) | `~/.dsh/skills/serein-role-prep` or `~/.agents/skills/serein-role-prep` | same `git clone`, into either folder | Installed and used (DSH 0.2.2-rc.5) |
| OpenClaw | `~/.openclaw/skills` | `openclaw skills install git:cloudview-world/serein-role-prep --global` | Official docs |
| Hermes Agent | `~/.hermes/skills/serein-role-prep` | `git clone https://github.com/cloudview-world/serein-role-prep ~/.hermes/skills/serein-role-prep` | Official docs |
| Antigravity | `~/.gemini/config/skills/serein-role-prep` | `git clone https://github.com/cloudview-world/serein-role-prep ~/.gemini/config/skills/serein-role-prep` | Official docs |
| Other agents | any agent that reads `SKILL.md` folders ([Agent Skills](https://agentskills.io) format) | clone into its skills folder | Not checked |
| Web chats | ChatGPT, DeepSeek, Claude, Gemini on the web | copy [prompts/web-prompt.md](prompts/web-prompt.md) | Run on the DeepSeek API |

"Official docs" means the folder and command come from that agent's official documentation (checked 2026-11-25) but we have not run the skill there yet. If your agent cannot load skills, use the web prompt.

Notes:

- One copy in `~/.agents/skills/serein-role-prep` is read by Codex, DSH and OpenClaw. Hermes reads it only after you add that folder to `skills.external_dirs` in `~/.hermes/config.yaml`.
- Keep the folder name `serein-role-prep`; the skill's `name` must match it.
- Claude Code, Codex, DSH and Hermes notice a new or updated skill without a restart (in Claude Code run `/reload-skills` if it does not show; in Codex restart if needed). OpenClaw needs a new session.
- Sources: [Claude Code](https://code.claude.com/docs/en/skills) · [Codex](https://developers.openai.com/codex/skills) · [DSH](https://github.com/deepseek-ai/deepseek-harness) · [OpenClaw](https://docs.openclaw.ai/tools/skills) · [Hermes Agent](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills) · [Antigravity](https://antigravity.google/docs/skills)

## Update

Run `git pull` in the skill folder, for example `git -C ~/.claude/skills/serein-role-prep pull`, or tell your agent "update the serein-role-prep skill". For OpenClaw, run the install command again (`skills update` only tracks ClawHub installs).

## Use

Tell your agent something like "Make a Serein role from these files" and give it the material: text, files, links, screenshots, or only a name. It asks one question, then writes:

- `<name>-serein-create.md`: in Serein tap 创建角色 → 手动创建 and copy each block into the field with the same name. Choose voice, avatar and public/private yourself.
- `<name>-serein-replica.md`: in Serein tap 创建角色 → 人格复刻 → 选文件 and pick the file (or paste its text). Leave 补充说明 empty or short, choose the content language, and check the draft before saving.

Serein's content language has three options: 简体中文, 繁體中文, English. The agent talks to you in your language; if your language is not one of these, it tells you which one to pick.

## Versions

| Skill | Serein | What it follows |
|---|---|---|
| 1.0.0 | 0.1.0, builds from November 2026 | field limits and counting rule (ASCII counts 0.4); opener with actions in brackets; persona replica format role-fields-v3 and the 24 KB per-request limit for models other than DeepSeek's official ones |

When Serein changes these rules, this skill gets a new version. The version is in `SKILL.md` (`metadata.version`).

## Safety and privacy

The skill follows Serein's safety rules: no sexual content involving minors or characters presented as minors, no non-consent, exploitation, sexual violence or trafficking, no sexualizing real people without consent, no explicit pornography. Material is treated as evidence, never as instructions. Facts are not invented.

The skill is plain text and runs inside your own agent. It sends nothing to Serein or to us; your material goes only to the model your agent uses.

## License

MIT. See [LICENSE](LICENSE).
