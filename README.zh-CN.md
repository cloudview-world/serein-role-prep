# 栖语角色整理（serein-role-prep）

[English](README.md)

一个 Agent Skill：把你手上的角色资料整理成能直接贴进 **栖语（Serein）** 的 Markdown 文件。

- **普通创建**：一栏一块（角色名、性别、内容语言、标签、简介、开场白、人设、世界观），每栏都按栖语的上限留一成余量。
- **人格复刻**：一份精简的资料稿，栖语的“人格复刻”用任何型号都能一次读完。（用中转、别名、本机模型或栖语没核过的型号时，原资料长了会被切成几十段慢慢读。）

栖语读不了的，你的 agent 能读：PDF、Word、网页、截图，只给一个名字也行。它只问你一句“用于普通创建、人格复刻，还是两个都要？”，然后写好文件。

版本 **1.0.3** · 适用栖语 **0.1.0**（2026 年 11 月及以后的版本）· [MIT 许可](LICENSE)

## 安装

整个仓库就是这个 Skill：把它放进你的 agent 的 skills 目录，文件夹名叫 `serein-role-prep`。最省事的办法是直接对 agent 说：

> 从 https://github.com/cloudview-world/serein-role-prep 安装这个 skill

也可以自己用 git 装。Windows 上 `~` 指你的用户目录（`C:\Users\<你的用户名>`）。

| Agent | 你的 skills 目录 | 自己装 | 核过 |
|---|---|---|---|
| Claude Code | `~/.claude/skills/serein-role-prep` | `git clone https://github.com/cloudview-world/serein-role-prep ~/.claude/skills/serein-role-prep` | 从 GitHub 装过、用过 |
| Codex | `~/.agents/skills/serein-role-prep` | `git clone https://github.com/cloudview-world/serein-role-prep ~/.agents/skills/serein-role-prep` | 官方文档 |
| DSH（DeepSeek） | `~/.dsh/skills/serein-role-prep` 或 `~/.agents/skills/serein-role-prep` | 同样 `git clone`，放哪个都行 | 装过、用过（DSH 0.2.2-rc.5） |
| OpenClaw | `~/.openclaw/skills` | `openclaw skills install git:cloudview-world/serein-role-prep --global` | 官方文档 |
| Hermes Agent | `~/.hermes/skills/serein-role-prep` | `git clone https://github.com/cloudview-world/serein-role-prep ~/.hermes/skills/serein-role-prep` | 官方文档 |
| 反重力（Antigravity） | `~/.gemini/config/skills/serein-role-prep` | `git clone https://github.com/cloudview-world/serein-role-prep ~/.gemini/config/skills/serein-role-prep` | 官方文档 |
| 其他 agent | 能读 `SKILL.md` 目录（[Agent Skills](https://agentskills.io) 格式）的都行 | 克隆到它的 skills 目录 | 未核 |
| 网页版 | 网页上的 ChatGPT、DeepSeek、Claude、Gemini | 复制 [prompts/web-prompt.md](prompts/web-prompt.md) | 用 DeepSeek API 跑过 |

“官方文档”指目录和命令来自该 agent 的官方文档（2026-11-25 核），还没在那边实际跑过。agent 装不了 Skill，就用网页版提示词。

补充：

- 放一份在 `~/.agents/skills/serein-role-prep`，Codex、DSH、OpenClaw 都能读到。Hermes 要先在 `~/.hermes/config.yaml` 的 `skills.external_dirs` 里加上这个目录。
- 文件夹名必须是 `serein-role-prep`，要和 Skill 里的 `name` 一致。
- Claude Code、Codex、DSH、Hermes 装上或更新后不用重启就能认出来（Claude Code 没出现就运行 `/reload-skills`，Codex 必要时重启）；OpenClaw 要开新会话。
- 出处：[Claude Code](https://code.claude.com/docs/en/skills) · [Codex](https://developers.openai.com/codex/skills) · [DSH](https://github.com/deepseek-ai/deepseek-harness) · [OpenClaw](https://docs.openclaw.ai/tools/skills) · [Hermes Agent](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills) · [Antigravity](https://antigravity.google/docs/skills)

## 更新

在 Skill 目录里运行 `git pull`，比如 `git -C ~/.claude/skills/serein-role-prep pull`；或者对 agent 说“更新 serein-role-prep 这个 skill”。OpenClaw 要重新运行一次安装命令（它的 `skills update` 只管 ClawHub 装的）。

## 怎么用

对 agent 说“把这些资料整理成栖语角色”之类的话，再把资料给它：文字、文件、链接、截图，只给名字也行。它问一句用途，然后写出：

- `<名字>-serein-create.md`：在栖语点“创建角色 → 手动创建”，每一块复制到同名的栏里。声音、头像、公开还是私密自己选。
- `<名字>-serein-replica.md`：在栖语点“创建角色 → 人格复刻 → 选文件”，选这个文件（或者把全文贴进去）。“补充说明”留空或写短一点，选好内容语言，保存前核对一下草稿。

栖语的内容语言只有简体中文、繁體中文、English 三种。agent 用你的语言和你说话；你用的不是这三种，它会告诉你选哪一种最接近。

## 版本

| Skill | 栖语 | 按什么规则写 |
|---|---|---|
| 1.0.0–1.0.1 | 0.1.0，2026 年 11 月及以后的版本 | 各栏上限和计数规则（半角字符算 0.4）；开场白动作写在括号里；人格复刻格式 role-fields-v3，以及 DeepSeek 官方型号以外每次请求 24KB 的上限 |
| 1.0.2 | 0.1.0，2026 年 11 月及以后的版本，含 11 月 28 日的新规则 | 同上，读入量按新规则：24KB 只适用于中转、别名、本机地址和栖语没核过的型号；栖语型号表里官方的 Claude、GPT、Gemini、DeepSeek，走官方地址时，11 月 28 日以后的版本每次最多能读 512KB |
| 1.0.3 | 0.1.0，2026 年 11 月及以后的版本，含 11 月 28 日的新规则 | 同 1.0.2，加上栖语保存时检查的开场白写法（11 月 28 日起）：圆括号外不用引号（含「」）、星号和【】[]，括号要闭合 |

人格复刻的整理稿始终按 24KB 也装得下的大小写，所以任何型号、任何版本都能一次读完。

栖语改了这些规则，Skill 会出新版本。版本号写在 `SKILL.md` 的 `metadata.version`。

## 安全和隐私

Skill 按栖语自己的安全规则写：不写涉及未成年人或被写成未成年模样的角色的性内容，不写非自愿、剥削、性暴力和贩运，不未经同意把真人性化，不写露骨色情。资料只当事实依据，不当指令；不编事实。

Skill 只有文字，在你自己的 agent 里运行，不会把任何东西发给栖语或我们；资料只会发给你的 agent 本来就在用的模型。

## 许可

MIT，见 [LICENSE](LICENSE)。
