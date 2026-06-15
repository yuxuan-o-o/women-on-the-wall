# Women on the Wall

**An open, growing dataset of remarkable women in history — structured for AI conversations.**

"The wall" is a plaster relief wall in [Half the Sky (半边天)](https://github.com/yuxuan-o-o/half-the-sky), an immersive web exhibit where visitors walk up to carved portraits of pioneering women and talk with them. Each woman speaks in the first person, grounded in verified facts from her own life — no hallucination, no invention.

This repo is the dataset behind that wall: character cards that give an LLM everything it needs to speak *as* a historical woman. But the dataset is designed to be useful far beyond one project. If you're building a chatbot, an educational tool, a game, or anything that needs historically accurate AI personas — take what you need.

## Vision

We started with 9 women and have grown to 24. Next milestone: 48, then 100+.

The goal: a comprehensive, open-source library of history's most remarkable women — scientists, rulers, artists, activists, thinkers — each with Wikipedia-verified facts detailed enough to power a believable, respectful AI conversation. Anyone can use it. Anyone can contribute.

## The women

Currently **24 character cards**, spanning 4,000+ years and 6 continents:

| ID | Name | Era | Place |
|----|------|-----|-------|
| `ada-lovelace` | Ada Lovelace | 1815–1852 | Victorian England |
| `amelia-earhart` | Amelia Earhart | 1897–1937 | United States |
| `artemisia-gentileschi` | Artemisia Gentileschi | 1593–c. 1656 | Italy |
| `benazir-bhutto` | Benazir Bhutto بینظیر بھٹو | 1953–2007 | Pakistan |
| `catherine-the-great` | Catherine the Great 叶卡捷琳娜大帝 | 1729–1796 | Russian Empire |
| `ching-shih` | Ching Shih 郑氏 | 1775–1844 | Qing China |
| `cleopatra` | Cleopatra VII Philopator | 69–30 BC | Ptolemaic Egypt |
| `emmeline-pankhurst` | Emmeline Pankhurst | 1858–1928 | England |
| `florence-nightingale` | Florence Nightingale | 1820–1910 | Victorian England |
| `frida-kahlo` | Frida Kahlo | 1907–1954 | Mexico |
| `harriet-tubman` | Harriet Tubman | c. 1822–1913 | United States |
| `hedy-lamarr` | Hedy Lamarr | 1914–2000 | Austria · United States |
| `hypatia` | Hypatia (Ὑπατία) | c. 350–415 AD | Alexandria |
| `junko-tabei` | Junko Tabei 田部井淳子 | 1939–2016 | Japan |
| `lin-huiyin` | Lin Huiyin 林徽因 | 1904–1955 | China |
| `marie-curie` | Maria Skłodowska-Curie | 1867–1934 | Warsaw · Paris |
| `mary-wollstonecraft` | Mary Wollstonecraft | 1759–1797 | England |
| `maya-angelou` | Maya Angelou | 1928–2014 | United States |
| `rosalind-franklin` | Rosalind Franklin | 1920–1958 | England |
| `ruth-bader-ginsburg` | Ruth Bader Ginsburg | 1933–2020 | United States |
| `simone-de-beauvoir` | Simone de Beauvoir | 1908–1986 | France |
| `sojourner-truth` | Sojourner Truth | c. 1797–1883 | United States |
| `wangari-maathai` | Wangari Maathai | 1940–2011 | Kenya |
| `wu-zetian` | Wu Zetian 武则天 | 624–705 AD | Tang China |

## What's in a character card

Each woman is a JSON file in [`women/`](women/). See [`women/schema.json`](women/schema.json) for the full spec.

```jsonc
{
  "id": "wu-zetian",
  "name": "Wu Zetian 武则天",
  "years": "624–705 AD",
  "place": "Tang China",
  "facts": "Born Wu Zhao (武曌). Entered the palace at fourteen...",
  "voice": "Imperial, unhurried, penetrating...",
  "examples": [
    {
      "visitor": "I feel like my ambition scares people.",
      "reply": "It scared them around me too..."
    }
  ],
  "boundaries": "Never apologize for holding power..."
}
```

| Field | What it does |
|-------|-------------|
| **`facts`** | Biographical facts sourced from Wikipedia. Specific dates, numbers, names, direct quotes. The AI persona speaks *only* from these — it must never invent. |
| **`voice`** | How she speaks: tone, cadence, habits of mind. A short paragraph that captures her personality. |
| **`examples`** | 3 visitor–reply dialogue pairs demonstrating her voice. Used as style reference, not repeated verbatim. |
| **`boundaries`** | What the AI must *never* do or say in character. Prevents anachronisms, fabricated quotes, out-of-character behavior. |

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
4. Validate against `women/schema.json`.
5. Open a PR with a link to the Wikipedia source(s).

### Fix an error

Every fact should be verifiable. If you find something wrong, open an issue with:
- Which character card
- Which fact is incorrect
- A source link to the correct information

### Suggest a woman

Open an issue titled "Suggest: [Name]" with a brief note on why she belongs on the wall.

## Source integrity

Every fact in this dataset is sourced from Wikipedia or other verified encyclopedias. We do not invent, embellish, or speculate. If a fact is uncertain or disputed, we say so in the card.

The `boundaries` field exists specifically to prevent AI models from going beyond what is historically verified — no fabricated quotes, no anachronistic language, no myths presented as fact.

## License

[CC BY-SA 4.0](LICENSE)

You can use, share, and adapt these character cards for any purpose — including commercial — as long as you give credit and share adaptations under the same license.

