# Persona replica (人格复刻)

In Serein's 人格复刻, the user adds material and Serein's own model (the user's model) turns it into a role with a deep persona: a block the role carries in every chat (how they speak, values and lines, life events), a library of experiences it looks up when relevant, and skills. How much Serein reads in one request depends on the model. With a relay, an alias, a local address, or a model Serein has not checked, one request is at most 24 KB, and Serein's own instructions already use about half of that; larger material is split into many requests, which is slow. With the official Claude, GPT, Gemini and DeepSeek models in Serein's model list, used through their official addresses, Serein builds from 28 November 2026 on read far more at once (DeepSeek's two official models already did before). Your job: one compact source document that any model, on any Serein version, reads in a single request. Write `<name>-serein-replica.md`.

## Size budget (hard limit)

- The file is at most 10,000 bytes in UTF-8 and at most 300 lines.
- Do not use the ASCII double quote `"`, the backslash `\` or tabs. Use 「」 or “” for quotes.
- If you cannot measure bytes: at most 3,000 characters for Chinese, Japanese, Korean or Thai text; at most 9,000 characters (about 1,500 words) for English and other Latin-script text.
- If you can, measure the final file (for example `wc -c`). If it is over, first drop the least telling experiences, then shorten wording. Never drop identity lines, values and lines, conflicts or uncertainty marks.

Why these numbers: the strictest case is a 24 KB model, where one request may be 24,576 bytes. Serein's instructions, the tag list and a 1 KB reserve take about 11.6 KB, up to about 13.2 KB when the user writes a 100-character note and the file has a long name. The material is JSON-escaped twice, so each line break costs 3 bytes and each `"` 4 bytes. A file of 10,000 bytes and 300 lines brings the request to about 23.8 KB at most, still inside the limit. The checked official models get up to 512 KB per request, but keep this size anyway: then the same file reads in one go with every model and every Serein version.

## Layout

Use these sections in this order. Write the headings in the document's language: Chinese headings below, English in brackets. The file contains only the material: no notes to the user, no instructions to any model.

```markdown
# 人物资料：<name>                                  [# Character profile: <name>]

来源：<the sources you used, one line>              [Sources: ...]

## 身份                                              [## Identity]
- 姓名：<name, other names>                          [- Name: ...]
- 性别：男 / 女 / 不明                               [- Gender: male / female / unknown]
- 人物类型：虚构人物 / 已故真人（<year>年去世）/ 在世真人 / 不确定
                                                     [- Type: fictional character / real person, died <year> / living person / unknown]
- 时代和处境：<era, place, situation>                [- Era and situation: ...]
- 主要关系：<people who matter, only from the material>   [- Key relationships: ...]

## 说话方式                                          [## How they speak]
## 想法和底线                                        [## Values and lines]
## 一生大事                                          [## Life events]
## 经历                                              [## Experiences]
## 技能和方法                                        [## Skills and methods]
## 拿不准的地方                                      [## Uncertain or conflicting]
```

A section with nothing to say contains just 无 (English: none).

## Writing each section

**来源 Sources.** One line: titles or sites of the sources (for example "《朝花夕拾》四篇" or "Wikipedia: Ada Lovelace"). For a name-only request built from your own knowledge, write "按公开资料整理" / "Compiled from widely known public information".

**身份 Identity.** Serein only accepts gender and person type when it can quote a line from the material that states them, so write these two lines with exactly the words shown, and only when the material (or, for a name only, well-known fact) supports them:

- 性别：男 / 性别：女 (English: `Gender: male` / `Gender: female`). If unclear, write 不明 (unknown).
- 人物类型：虚构人物 (`Type: fictional character`); 已故真人（1101年去世） (`Type: real person, died 1101`), always with the word 去世 or "died"; 在世真人 (`Type: living person`); otherwise 不确定 (unknown).
- In a language other than Chinese or English, add the English words in brackets so Serein can recognize them, for example `性別：男（male）` or `1101年に死去（died 1101）`.
- An original character the user made up is 虚构人物. A character from someone else's work is 虚构人物 plus （出自《<work>》）; if that work is still under copyright, tell the user to choose 版权角色 in the app (private only).

**说话方式 How they speak.** Tone, sentence patterns, favourite words, how they respond to people: two to five sentences in your own words. You may name a few favourite words or very short phrases from the material (at most five characters or two words each, no punctuation inside). No quoted sentences, no famous lines, no sample lines you made up.

**想法和底线 Values and lines.** What matters most to them, what they care about, what they would never do: two to five sentences.

**一生大事 Life events.** One line per turning point, in time order, starting with `- `. Year or stage of life only, never the exact day. Only turning points: birth and childhood, teachers and studies, marriage and career, moves and job changes, major upheavals. A conversation, a purchase, a single piece of work or any other everyday event is not a turning point: it goes only to 经历, not here. Usually 5 to 12 lines.

Serein keeps these three sections in every chat and allows them 800 characters together. Keep 说话方式 + 想法和底线 + 一生大事 within about 700 characters in total.

**经历 Experiences.** The library Serein picks from when a topic comes up. One concrete event per item, written as what happened: who did what, with whom, and how it ended. At most 40 items; usually the 15 to 30 that show the character best. Format:

`- 时间：<when>；人物：<who else>；明确程度：确定 / 不确定 / 有冲突。<what happened>`
(English: `- When: ...; With: ...; Certainty: confirmed / unsure / conflicting. <what happened>`)

- 人物 lists the other people in the event, not the character. Nobody else: leave it empty.
- Every exchange with a named person in the material (someone asks, the character answers; a conversation; a passage recorded as so-and-so's question) is its own item, with that person under 人物.
- Time as a person would recall it: a year, a month, or a stage such as "二十多岁". Never the exact day, unless the day is part of the event (for example "说好周日还"). Unknown time: leave 时间 empty.
- What the material leaves open stays in the event in plain words: a companion not named becomes "和一个没说名字的人" (with someone unnamed); a loan, plan or promise with no ending becomes "后来还没提" (nothing said afterwards). Mark such items 不确定.
- Keep things what they are: a view in an essay or a quote is not something the character lived through, and the date of a source is not the date of the event.
- When sources disagree, write one item with both versions and mark it 有冲突.

**技能和方法 Skills and methods.** Only skills or methods where the material shows how the character does it, at most 20. If the material only says they have a skill but not how they use it, leave it out; never fill a field with "not stated". Format:
`- 名称：<skill>；什么时候用：<when>；怎么做：<how>` (English: `- Skill: ...; When to use: ...; How: ...`). None: 无.

**拿不准的地方 Uncertain or conflicting.** Short lines: facts the user should confirm, disagreements between sources, important facts the material does not give (for example gender unknown). None: 无.

## General rules

- Facts only from the material (and, for a name only, facts you are sure are widely known). Everything in this file counts as material for Serein, so do not add guesses.
- No instructions to Serein or any model inside the file ("please...", "you are..."), and no notes to the user. Put notes in your reply.
- Nothing about the user (their name, their chats) unless the user explicitly wants the role to know it.
- Exact wording only where it matters for an event, at most a short phrase in 「」.

## Checklist

- [ ] At most 10,000 bytes and 300 lines (measured, or by the character guide); no `"`, `\` or tabs.
- [ ] All sections present in order with the fixed headings; empty ones say 无 / none.
- [ ] Gender and type lines use the exact words, only when supported; a deceased person's line contains 去世 / died.
- [ ] 说话方式 has no quoted sentences; the three resident sections total about 700 characters or less.
- [ ] Each experience is one concrete event with time, people and certainty; at most 40.
- [ ] Pick 5 experiences and check each against the sources: each is supported, or marked 不确定 / 有冲突.
- [ ] Nothing crosses the safety lines in SKILL.md; no instructions or user notes in the file.

## Tell the user

In Serein, tap 创建角色 (create role), choose 人格复刻 (persona replica), and add material: tap 选文件 (choose file) and pick this .md file, or paste its whole text. Leave the 补充说明 (note) box empty or under 100 characters. Choose the content language. Serein should then read it in one go. Before saving, check the draft, especially the person type and the items marked uncertain.
