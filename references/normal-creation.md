# Normal creation (普通创建)

The user creates the role by hand in Serein ("create role" form) and copies each block of your file into the field with the same name. Write `<name>-serein-create.md` with the template at the end of this file.

## Fields and limits

Write at most the "Write at most" column. It keeps a 10% margin below Serein's limit.

| Field (app label) | Required | Serein accepts | Write at most | What it is for |
|---|---|---|---|---|
| 角色名 Name | yes | 16 name units | 14 name units | the role's name |
| 性别 Gender | yes | 男 / 女 / 不指定 | one of the three | |
| 内容语言 Content language | yes | 简体中文 / 繁體中文 / English | one of the three | see SKILL.md "Languages" |
| 题材标签 Tags | no | up to 3 from the app's list | up to 3 | browsing |
| 简介 Intro | yes | 300, and 500 characters raw | 270, and 450 characters raw | shown on the role card only; the chat AI never reads it |
| 开场白 Opener | yes | 10 to 300 | 10 to 270 | the role's first message |
| 人设 Persona | yes | 20 to 3000 | aim for 300 to 800; never over 2700 | the chat AI reads it on every turn |
| 世界观 Worldview | no | up to 1000 | 900 | the setting, only if the material gives one |

Voice, avatar, cover image and public/private are set by the user in the app. Do not write them.

## How Serein counts

Text fields (Intro, Opener, Persona, Worldview). Remove spaces and line breaks at the start and end first, then:

- every printable ASCII character counts 0.4: English letters, digits, the space, half-width punctuation (code points U+0020 to U+007E);
- everything else counts 1 per UTF-16 code unit: Chinese, Japanese and Korean characters, full-width punctuation such as ，。！（）, line breaks, accented letters such as é, every Thai letter and every Thai vowel or tone mark separately;
- most emoji count 2;
- round the total up.

Examples: `Hello, 世界！` = 6. 300 Chinese characters = 300. 750 English letters = 300. `a`, line break, `b` = 2.

Name: remove spaces at the start and end, then count each visible character: 1 if it is a single printable ASCII character, otherwise 2. So 8 Chinese characters = 16, `Elizabeth Bennet` = 16, the middle dot `·` = 2, a Thai letter with its vowel or tone marks = 2.

The Intro must also be at most 450 characters in plain length (Serein's hard cap is 500).

If you cannot run code: count every character as 1 and every emoji as 2. This never counts too low, so text that passes this way is safe.

## Writing each field

**角色名 Name.** The name the role is called by. If it is too long, use the common short form of the name (for example the family name plus given name without titles). Do not invent a nickname.

**性别 Gender.** 男, 女 or 不指定. Choose 男 or 女 only when the material says so (or, for a named public figure, when it is well known). If unclear, 不指定.

**内容语言 Content language.** 简体中文, 繁體中文 or English, following SKILL.md "Languages".

**题材标签 Tags.** 0 to 3 tags that clearly fit, only from Serein's current list (the user taps them in the app). Each tag is shown as 简体中文 / 繁體中文 / English:

| 简体中文 | 繁體中文 | English |
|---|---|---|
| 古风 | 古風 | Ancient Style |
| 现代 | 現代 | Modern |
| 科幻 | 科幻 | Sci-Fi |
| 治愈 | 療癒 | Healing |
| 武侠 | 武俠 | Wuxia |
| 校园 | 校園 | Campus |
| 奇幻 | 奇幻 | Fantasy |
| 悬疑 | 懸疑 | Mystery |
| 都市 | 都市 | Urban |
| 哲思 | 哲思 | Philosophical |

Copy the names exactly from the column of the chosen content language. Do not translate them into another language and do not invent tags. If none fits, leave the block empty; the app then files the role under General. The list can change, so say in Notes that the user picks the tags in the app.

**简介 Intro.** One to three sentences for someone browsing roles: who this is and what kind of person. No "based on the material", no report tone. Do not put anything here that the chat AI needs to know; it never reads this field.

**开场白 Opener.** The first thing the role says when meeting the user. The user is meeting the role for the first time. Serein checks the opener's format with a fixed rule when the role is saved; if it fails, the author is asked to tidy it with their own model first. Write it so it passes.

- Actions, expressions and scene go in round brackets: full-width （） in Chinese and Japanese, half-width () in English (Serein accepts both). Close every bracket you open.
- Inside the brackets write a short action. For the role's own action leave out the subject; for the user write 你 / you. Never 她 / 他 / she / he or the role's name. For example （放下手里的笔，抬头看你） or (sets the kettle down).
- Outside the brackets write only what the role says aloud, in the first person, with no marks around it. Outside the brackets Serein rejects paired quote marks (“” "" 「」 『』 ‘’ ''), paired asterisks (`*…*` `＊…＊`) and the marks 【】 [] ［］ 〔〕 〖〗. Inside the brackets they are not checked.
- An apostrophe (I'm, don't, students') is not a quote mark. Put titles of books, songs and films in 《》.
- These also fail, so avoid them: quote marks around a single word in the speech (你也喜欢“星空”吗), emoticons such as `:(` and `*` used as a multiplication sign.
- Japanese: 「」 and 『』 count as quote marks too. Do not wrap the role's lines in 「」; write them bare outside the brackets.
- No third-person narration such as 她笑着说 or "He looks up at you", inside or outside the brackets.
- Do not invent a past with the user: no "long time no see", no shared memories, no earlier promises. Do not assume the user's name, gender or situation.
- Make it fit this role's personality and situation. No generic greeting.
- At least 10 characters.

Good: `（把茶盏推到你面前）坐吧。外面雨大，先喝口热的。`
Good: `(closes the ledger) You're letting the cold in. Shut the door and tell me what you need.`
Good: `（手を止めて、顔を上げる）いらっしゃい。外、寒かったでしょう。こっちで温まっていって。`
Bad: `她微笑着看向你：“好久不见，你终于回来了。”` (narration, quote marks, invented past)
Bad: `*smiles* Hello, you made it.` (asterisks; write `(smiles) Hello, you made it.`)
Bad: `你也喜欢“星空”这首歌吗？我常听。` (quote marks around a word; write 《星空》)

**人设 Persona.** What the chat AI reads on every turn; it must be enough on its own to play the role well. Write it in the third person as a description of the role (for example "沈砚秋是……" or "Holmes is..."), not as "You are...". Include:

- the name, and who the role is (identity, era or situation);
- personality and what the role values;
- how the role talks: tone, sentence patterns, favourite words, how they respond to people. Describe it in your own words. You may name a few favourite words or very short phrases from the material (at most five characters or two words each); do not quote whole sentences or invent sample lines;
- the relationship to the user and its limits, only if the material or the user says so. Otherwise write nothing about it (no "the relationship is not set");
- uncertain facts stay uncertain ("never confirmed whether...").

Do not copy the Intro. Do not paste the source text. Aim for 300 to 800; go longer only when the material is rich, never over 2700.

**世界观 Worldview.** The world the role lives in (era, place, how a fictional world works), only as far as the material states it. If the material gives no setting, leave the block empty. Do not add "modern times" or similar on your own.

## Template

Each field is a fenced `text` block, so chat apps and Markdown viewers show a copy button. The file starts with the title line and has nothing before it.

````markdown
# <Name> · Serein role card (normal creation)

Made with serein-role-prep 1.0.3 for Serein 0.1.0. Copy each block into the field with the same name.

## 角色名 Name
```text
<name>
```

## 性别 Gender
```text
<男 / 女 / 不指定>
```

## 内容语言 Content language
```text
<简体中文 / 繁體中文 / English>
```

## 题材标签 Tags (tap in the app, up to 3)
```text
<tag>、<tag>
```

## 简介 Intro
```text
<intro>
```

## 开场白 Opener
```text
<opener>
```

## 人设 Persona
```text
<persona>
```

## 世界观 Worldview (optional)
```text
<worldview, or leave empty>
```

## Notes (do not paste)
- Counts by Serein's rule: Name <n>/16 · Intro <n>/300 · Opener <n>/300 · Persona <n>/3000 · Worldview <n>/1000
- <defaults you chose, things to confirm, what was left out and why>
````

Write the Notes in the user's language.

## Checklist

- [ ] Name, Gender, Content language, Intro, Opener and Persona are all filled.
- [ ] Every count is within "Write at most", counted by Serein's rule or the safe fallback, and the counts are in Notes.
- [ ] Opener: actions in brackets and every bracket closed; outside the brackets only the role's spoken words, with no paired quote marks (「」 included), no paired asterisks and no 【】 or [] marks; no she / he or role name inside the brackets; no invented past with the user; at least 10 characters.
- [ ] Gender and every fact can be traced to the material (or, for a name only, to well-known facts); uncertain things are marked.
- [ ] Tags are from the list, at most 3.
- [ ] Nothing crosses the safety lines in SKILL.md.

## Tell the user

In Serein, tap 创建角色 (create role), choose 手动创建 (manual creation), and copy each block into the field with the same name. Pick voice, avatar and public/private yourself. If the role is a living real person or a character from someone else's copyrighted work, keep it private.
