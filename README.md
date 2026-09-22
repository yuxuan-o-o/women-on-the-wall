# Women on the Wall

**An open, growing dataset of remarkable women in history — structured for AI conversations.**

"The wall" is a plaster relief wall in [Half the Sky (半边天)](https://halfthesky.app), an immersive web exhibit where visitors walk up to carved portraits of pioneering women and talk with them. Each woman speaks in the first person, grounded in verified facts from her own life — no hallucination, no invention.

This repo is the dataset behind that wall: character cards that give an LLM everything it needs to speak *as* a historical woman. But the dataset is designed to be useful far beyond one project. If you're building a chatbot, an educational tool, a game, or anything that needs historically accurate AI personas — take what you need.

## Vision

We started with 9 women, grew to 24, and are now at 36 — 32 of them on the wall. Next milestone: 48, then 100+.

The goal: a comprehensive, open-source library of history's most remarkable women — scientists, rulers, artists, activists, thinkers — each with Wikipedia-verified facts detailed enough to power a believable, respectful AI conversation. Anyone can use it. Anyone can contribute.

## The women

Currently **36 character cards** (32 on the wall), spanning 4,000+ years and 6 continents:

| ID | Name | Era | Place |
|----|------|-----|-------|
| `ada-lovelace` | Ada Lovelace | 1815–1852 | Victorian England |
| `amelia-earhart` | Amelia Earhart | 1897–1937 | United States |
| `artemisia-gentileschi` | Artemisia Gentileschi | 1593–c. 1656 | Italy |
| `begum-rokeya` | Begum Rokeya Sakhawat Hossain রোকেয়া সাখাওয়াৎ হোসেন | 1880–1932 | Bengal under British rule · Pairaband · Bhagalpur · Calcutta |
| `benazir-bhutto` | Benazir Bhutto بینظیر بھٹو | 1953–2007 | Pakistan |
| `bertha-lutz` | Bertha Lutz | 1894–1976 | Brazil · São Paulo · Rio de Janeiro · Paris · San Francisco |
| `catherine-the-great` | Catherine the Great 叶卡捷琳娜大帝 † | 1729–1796 | Russian Empire |
| `ching-shih` | Zheng Yi Sao 郑一嫂 † | 1775–1844 | Qing China |
| `clara-zetkin` | Clara Zetkin | 1857–1933 | Germany · Zurich · Paris · Stuttgart · Berlin · Moscow |
| `cleopatra` | Cleopatra VII Philopator † | 69–30 BC | Ptolemaic Egypt |
| `elizabeth-garrett-anderson` | Elizabeth Garrett Anderson | 1836–1917 | Victorian & Edwardian England · London · Aldeburgh |
| `emmeline-pankhurst` | Emmeline Pankhurst | 1858–1928 | Manchester and London, England |
| `florence-nightingale` | Florence Nightingale | 1820–1910 | Victorian England |
| `frida-kahlo` | Frida Kahlo | 1907–1954 | Mexico |
| `funmilayo-ransome-kuti` | Funmilayo Ransome-Kuti | 1900–1978 | Abeokuta · Lagos, Nigeria |
| `harriet-tubman` | Harriet Tubman | c. 1822–1913 | United States |
| `hedy-lamarr` | Hedy Lamarr † | 1914–2000 | Austria · United States |
| `huda-shaarawi` | Huda Sha'arawi هدى شعراوي | 1879–1947 | Egypt under British occupation · Cairo · Rome |
| `hypatia` | Hypatia (Ὑπατία) | c. 350–415 AD | Alexandria |
| `junko-tabei` | Junko Tabei 田部井淳子 | 1939–2016 | Japan |
| `kate-sheppard` | Kate Sheppard | c. 1847–1934 | Colonial New Zealand · Christchurch |
| `lin-huiyin` | Lin Huiyin 林徽因 | 1904–1955 | China |
| `lin-qiaozhi` | Lin Qiaozhi 林巧稚 | 1901–1983 | China · Gulangyu, Xiamen · Beijing |
| `marie-curie` | Maria Skłodowska-Curie (Marie Curie) | 1867–1934 | Warsaw · Paris |
| `mary-wollstonecraft` | Mary Wollstonecraft | 1759–1797 | England |
| `maya-angelou` | Maya Angelou | 1928–2014 | United States |
| `olympe-de-gouges` | Olympe de Gouges | 1748–1793 | Montauban · Paris, Revolutionary France |
| `rosalind-franklin` | Rosalind Elsie Franklin | 1920–1958 | London · Paris · London |
| `ruth-bader-ginsburg` | Ruth Bader Ginsburg | 1933–2020 | United States |
| `shirley-chisholm` | Shirley Chisholm | 1924–2005 | United States · Brooklyn, New York · Washington, D.C. |
| `simone-de-beauvoir` | Simone de Beauvoir | 1908–1986 | France |
| `sojourner-truth` | Sojourner Truth | c. 1797–1883 | United States |
| `sor-juana` | Sor Juana Inés de la Cruz | 1648 or 1651–1695 | Viceroyalty of New Spain · Nepantla · Mexico City |
| `wangari-maathai` | Wangari Maathai | 1940–2011 | Kenya |
| `wu-zetian` | Wu Zetian 武则天 | 624–705 AD | Tang China |
| `zheng-yuxiu` | Zheng Yuxiu 郑毓秀 | 1891–1959 | Republican China · Paris · Shanghai |

† `on_wall: false` — kept in the dataset, not currently shown on the Half the Sky wall.

## What's in a character card

Each woman is a JSON file in [`women/`](women/). See [`women/schema.json`](women/schema.json) for the full spec.

```jsonc
{
  "id": "wu-zetian",
  "name": "Wu Zetian 武则天",
  "years": "624–705 AD",
  "place": "Tang China",
  "facts": "Her given name at birth is not recorded; in 689 she took the name Zhao (曌), a character she coined herself. Entered the palace at fourteen...",
  "voice": "Imperial, unhurried, penetrating...",
  "examples": [
    {
      "visitor": "I feel like my ambition scares people.",
      "reply": "It scared them around me too..."
    }
  ],
  "boundaries": "Never apologize for holding power...",
  "misconceptions": ["That she was born Wu Zhao (武曌) — her birth name is not recorded; she coined the character 曌 and took it as her name in 689."],
  "quote_note": "...",      // optional: where her quoted line comes from, verbatim or rendered
  "on_wall": true,          // optional: false = in the dataset, not on the Half the Sky wall
  "sources": [
    { "label": "《旧唐书》礼仪志", "url": "https://ctext.org/...", "kind": "一手" }
  ],
  "fact_check": {
    "date": "2026-08-19",
    "rounds": 3,
    "corrections": ["武举始于 702 年，非 690 年代"],
    "additions": ["688 年洛阳明堂"]
  }
}
```

| Field | What it does |
|-------|-------------|
| **`facts`** | Biographical facts, each checkable against the card's `sources`. Specific dates, numbers, names, direct quotes. The AI persona speaks *only* from these — it must never invent. |
| **`voice`** | How she speaks: tone, cadence, habits of mind. A short paragraph that captures her personality. |
| **`examples`** | 3 visitor–reply dialogue pairs demonstrating her voice. Used as style reference, not repeated verbatim. |
| **`boundaries`** | What the AI must *never* do or say in character. Prevents anachronisms, fabricated quotes, out-of-character behavior. |
| **`misconceptions`** | Widespread false claims about her, each paired with what the record shows. Given to the persona so she can correct them in her own voice. |
| **`quote_note`** | *(optional)* Where the card's quoted line comes from, and whether it is verbatim or a rendering. |
| **`on_wall`** | *(optional)* `false` marks a card that stays in the dataset but is not currently shown on the Half the Sky wall. Absent means `true`. |
| **`sources`** | Where the facts were checked. Every link is HTTP-checked before it goes in. Ordered by weight: `primary` → `official` → `institution` → `scholarly` → `reference` → `press`. |
| **`fact_check`** | Provenance of the last review: date, how many passes, what was corrected, what had been missing. |

Provenance fields are **bilingual**. English is canonical; `summary_zh`, `corrections_zh`, `additions_zh`, `kind_zh` and `note_zh` carry the Chinese. The `facts`, `voice`, `examples` and `boundaries` fields stay English-only for now — translating them is open work, see Contributing.

## Quick start

**Python:**
```python
import json
from pathlib import Path

women = {}
for p in Path("women").glob("*.json"):
    if p.name == "schema.json":
        continue
    card = json.load(open(p))
    women[card["id"]] = card

# Use with any LLM
system_prompt = f"""You are {card['name']}.
Facts (speak only from these): {card['facts']}
Voice: {card['voice']}
Boundaries: {card['boundaries']}"""
```

**JavaScript / fetch:**
```js
const card = await fetch('women/wu-zetian.json').then(r => r.json());
```

**Direct download:**
```bash
curl -O https://raw.githubusercontent.com/yuxuan-o-o/women-on-the-wall/main/women/wu-zetian.json
```

## Contributing

### Add a new character

1. Pick a remarkable woman not yet in the dataset.
2. Research her life on **Wikipedia** (or another verified encyclopedia).
3. Create `women/her-slug.json` following the schema:
   - **`facts`**: specific dates, numbers, names, and direct quotes. No vague summaries. Every claim must be traceable to a Wikipedia article.
   - **`voice`**: a short description of *how* she speaks — not what she says, but how she says it.
   - **`examples`**: 3 dialogue pairs (visitor question + her answer), grounded in the facts.
   - **`boundaries`**: what the AI must never do in her voice — anachronisms to avoid, common myths to reject, tone violations to prevent.
   - **`misconceptions`**: the myths people actually repeat about her, each with what the record shows. One to three; `[]` if none are genuinely widespread.
   - **`sources`**: at least one checkable link per card, strongest available. Wikipedia is acceptable as a starting point, but prefer the archive, museum, court record, university or prize body it cites.
4. Validate against `women/schema.json`.
5. Open a PR. Every factual claim in the card should be traceable to something in `sources`.

### Fix an error

Every fact should be verifiable. If you find something wrong, open an issue with:
- Which character card
- Which fact is incorrect
- A source link to the correct information

### Suggest a woman

Open an issue titled "Suggest: [Name]" with a brief note on why she belongs on the wall.

## Source integrity

Every card now carries a `sources` array. Previously the dataset claimed Wikipedia verification but shipped no links, so nothing could be checked by a reader. That gap was closed in August 2026 — **66 sources across 24 cards** — and the dataset now carries **213 sources across 36 cards**, every URL HTTP-checked. Twelve of them (British Museum, Britannica, Library of Congress, Smithsonian, Science Museum, NGA, Wiley, ResearchGate) block automated requests and return 403; those were confirmed by opening them in a real browser and are flagged with a `note`.

We do not invent, embellish, or speculate. Where a claim is contested, the card keeps the hedge rather than picking the cleaner-sounding version.

### What the August 2026 review changed

Three independent passes over all 24 cards. The recurring problems were not typos — they were structural:

- **Team results written as solo achievements.** The 2,738 buildings surveyed by the Society for the Study of Chinese Architecture had been credited to Lin Huiyin and Liang Sicheng alone. Photo 51 belongs to Franklin *and* Raymond Gosling.
- **Overconfident "first / only".** Claims were kept only where a definition and an authority support them, and hedged everywhere else.
- **Technical ancestry stated as descent.** Bluetooth does use frequency hopping; Wi-Fi and GPS do not. Hedy Lamarr's patent is their conceptual relative, not their ancestor.
- **Achievements missing entirely.** Institutions these women built, second careers they held, formal offices they occupied, and what they had already done *before* the famous event.
- **Myth quoted as record.** Sojourner Truth almost certainly never said "Ain't I a Woman?" — that refrain comes from Frances Gage's 1863 retelling, twelve years after the speech.

Eight factual corrections and ten sets of restored achievements were applied. Each card's `fact_check` field records what changed in that specific card.

The `boundaries` field still exists to stop models going beyond what is verified — no fabricated quotes, no anachronistic language, no myths presented as fact.

### What changed in September 2026

- **Round 4 (3 Sept).** Every card was levelled against the exhibit's independently audited timeline — 87 corrections and 52 additions across the 24 cards — and gained a `misconceptions` field, so the persona is told which myths to correct rather than left to discover them.
- **Twelve new women (17 Sept), in two batches.** Zheng Yuxiu 郑毓秀, Olympe de Gouges, Huda Sha'arawi, Kate Sheppard, Funmilayo Ransome-Kuti, Shirley Chisholm; then Bertha Lutz, Begum Rokeya, Sor Juana Inés de la Cruz, Clara Zetkin, Elizabeth Garrett Anderson, Lin Qiaozhi 林巧稚. Each was researched from primary, official and scholarly sources first (Wikipedia at most once per card), then fact-checked in two independent rounds before merging. Every "first / only" without an official source is hedged.
- **Four cards stepped off the wall.** Cleopatra, Catherine the Great, Zheng Yi Sao and Hedy Lamarr stay in the dataset with `on_wall: false`; the exhibit now selects for women who advanced rights or education and whose achievements were their own. `ching-shih` was renamed to Zheng Yi Sao 郑一嫂 (id unchanged).
- **Schema** gained `on_wall` and `quote_note`.

## 中文说明

**Women on the Wall** 是一个开放的历史女性数据集，为 AI 角色对话设计。每位女性一张 JSON 角色卡，包含可核查的生平事实、说话方式、示例对话与行为边界，供任何聊天机器人、教育工具或游戏使用。

目前 **36 张卡**（其中 32 位在 Half the Sky 的墙上），**213 条来源**，每个链接都验活过。

### 2026 年 8 月这轮核查改了什么

数据集此前声称「事实均来自维基百科核实」，但**没有任何来源字段**，读者无法核对任何一条。这一轮补上了：**24 张卡、66 条来源，每个链接都发起过 HTTP 请求验活**；其中 12 条（大英博物馆、Britannica、美国国会图书馆、Smithsonian 等）拦截自动请求，已用真实浏览器确认可达，并在 `note` 中标注。

三轮独立核查发现的问题不是错别字，而是结构性的：

- **团队成果被写成个人独力完成**——营造学社测绘的 2,738 处古建筑曾被归到林徽因与梁思成两人名下；Photo 51 属于 Franklin 与 Raymond Gosling 共同完成。
- **过硬的「第一／唯一」**——只在定义明确且有权威来源支持时保留，其余一律加限定语。
- **把技术近亲写成直接谱系**——Bluetooth 确实使用跳频，Wi-Fi 与 GPS 不是；Hedy Lamarr 的专利是它们的概念亲戚，不是祖先。
- **成就整块缺失**——她们建立的机构、从事的第二职业、担任的正式职位，以及成名事件**之前**就已做成的事。
- **把传说当记录引用**——Sojourner Truth 几乎可以确定从未说过「Ain't I a Woman?」，那句叠句出自 Frances Gage 在演讲十二年后（1863）的重述。

共应用 **8 处事实修正**与 **10 张卡的成就补全**。每张卡的 `fact_check` 字段记录了这张卡具体改了什么，中英文对照。

### 2026 年 9 月改了什么

- **第四轮（9 月 3 日）**：全部 24 张卡与展览独立审定的年表逐条对齐，共 87 处修正、52 处补充；新增 `misconceptions` 字段——把关于她的常见误传直接告诉角色，让她在对话里自己纠正，而不是等她「碰巧」知道。
- **新增 12 位（9 月 17 日，分两批）**：郑毓秀、Olympe de Gouges、Huda Sha'arawi、Kate Sheppard、Funmilayo Ransome-Kuti、Shirley Chisholm；Bertha Lutz、Begum Rokeya、Sor Juana Inés de la Cruz、Clara Zetkin、Elizabeth Garrett Anderson、林巧稚。每位先以一手／官方／学术来源研究（维基百科每张卡至多引一次），再经两轮独立核查后合并；没有官方来源支持的「第一／唯一」一律加限定语。
- **四张卡退出墙面**：Cleopatra、Catherine the Great、郑一嫂、Hedy Lamarr 保留在数据集中，标记 `on_wall: false`——展览现在只选推动过女性权利或教育、且成就出于自身的女性。`ching-shih` 更名为 Zheng Yi Sao 郑一嫂（id 不变）。
- **schema** 新增 `on_wall`、`quote_note`。

### 想贡献？

欢迎补新人物、修错、或把 `facts`／`voice`／`examples`／`boundaries` 翻成中文——目前这四个字段仍是英文。提 PR 时请确保卡里每一条陈述都能追溯到 `sources` 里的某个链接。发现错误也可以直接开 issue，注明是哪张卡、哪一条、以及正确信息的来源链接。

## License

[CC BY-SA 4.0](LICENSE)

You can use, share, and adapt these character cards for any purpose — including commercial — as long as you give credit and share adaptations under the same license.

