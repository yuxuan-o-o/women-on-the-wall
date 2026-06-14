# Women on the Wall

An open dataset of historical women, built for AI persona conversations.

Each character card contains **Wikipedia-verified biographical facts**, a voice description, example dialogues, and character boundaries — everything an LLM needs to speak *as* a historical woman without hallucinating.

Built for [Half the Sky (半边天)](https://github.com/yuxuan-o-o/half-the-sky), an immersive web exhibit where visitors talk with pioneering women carved in plaster relief.

## The women (v1)

| ID | Name | Era | Place |
|----|------|-----|-------|
| `ada-lovelace` | Ada Lovelace | 1815–1852 | Victorian England |
| `frida-kahlo` | Frida Kahlo | 1907–1954 | Mexico |
| `hypatia` | Hypatia (Ὑπατία) | c. 350–415 AD | Alexandria |
| `lin-huiyin` | Lin Huiyin 林徽因 | 1904–1955 | China |
| `marie-curie` | Maria Skłodowska-Curie | 1867–1934 | Warsaw · Paris |
| `ruth-bader-ginsburg` | Ruth Bader Ginsburg | 1933–2020 | United States |
| `sojourner-truth` | Sojourner Truth | c. 1797–1883 | United States |
| `wangari-maathai` | Wangari Maathai | 1940–2011 | Kenya |
| `wu-zetian` | Wu Zetian 武则天 | 624–705 AD | Tang China |

## Data format

Each woman is a JSON file in `women/`. See [`women/schema.json`](women/schema.json) for the full spec.

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

**Fields:**

- **`facts`** — Biographical facts sourced from Wikipedia. The AI persona speaks *only* from these; it must never invent.
- **`voice`** — How she speaks: tone, cadence, habits of mind.
- **`examples`** — Visitor–reply pairs demonstrating her voice (used as style reference, not repeated verbatim).
- **`boundaries`** — What the AI must *never* do or say in character (prevents anachronisms, fabricated quotes, out-of-character behavior).

## Using the data

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
```

**JavaScript:**
```js
const cards = await Promise.all(
  ['wu-zetian', 'frida-kahlo', 'hypatia'].map(id =>
    fetch(`women/${id}.json`).then(r => r.json())
  )
);
```

## Contributing a new character

1. Research her life on Wikipedia (or another verified encyclopedia).
2. Write `facts` with **specific dates, numbers, names, and direct quotes**. No vague summaries.
3. Write `voice` — a short description of *how* she speaks.
4. Write 3 `examples` — visitor questions + her answers, grounded in the facts.
5. Write `boundaries` — what the AI must never do in her voice.
6. Validate against `women/schema.json`.
7. Open a PR.

## Source integrity

Every fact in this dataset comes from Wikipedia or other verified encyclopedias. If you find an error, please open an issue with a source link.

## License

Data: [CC BY-SA 4.0](LICENSE)

This means you can use, share, and adapt the character cards for any purpose — including commercial — as long as you give credit and share adaptations under the same license.
