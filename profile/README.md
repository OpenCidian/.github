# OpenCidian

An open Chinese ↔ Vietnamese dictionary that people, apps and AI models can read: Hán Việt readings, pinyin, Vietnamese and English meanings, and how each character is built.

The name: 词典 *cídiǎn* and 詞典 *từ điển* are the same word, read in Mandarin and in Hán Việt.

## Why

There is no open dataset, public API or MCP server for Chinese → Vietnamese. The Vietnamese dictionary sites have no API, and the Chinese dictionary MCPs answer only in Chinese or English. OpenCidian puts the open sources together in one dataset, says where every value came from, and lets anyone suggest a fix.

## What a word looks like

```jsonc
{
  "simp": "觉得", "trad": "覺得", "pinyin": "jué de",
  "hanviet": [
    { "char": "觉", "trad": "覺", "readings": ["giác", "giáo"], "src": "thieu-chuu" },
    { "char": "得", "readings": ["đắc"], "src": "thieu-chuu" }
  ],
  "vi": { "senses": ["nghĩ rằng ...; cảm thấy rằng ..."], "src": "cvdict" },
  "en": { "senses": ["to think that ...; to feel that ..."], "src": "cc-cedict" },
  "hsk": { "hsk2": 2, "hsk3": 1, "src": "hsk" }
}
```

Every character of a compound gets its Hán Việt readings, not only the first. Characters have their own record: radical, stroke count, breakdown, and the meaning and sound parts, each with its own Hán Việt reading.

The first build holds 125,397 words and 14,534 characters.

## Repositories

| Repo | What it is |
|---|---|
| `opencidian-data` | The pinned sources, the community corrections, and the build that turns them into one dataset, published as GitHub releases |
| `opencidian-api` | The API over the dataset (Cloudflare Workers and D1): lookup by hanzi, pinyin or Vietnamese, characters, reverse search by meaning, text annotation |
| `opencidian-mcp` | The public MCP server, so AI assistants can look words up instead of guessing |

The repositories open to the public once the MCP server is ready.

## Sources

| Source | Gives | Licence |
|---|---|---|
| [CC-CEDICT](https://cc-cedict.org/wiki/) | words, pinyin, English, classifiers | CC BY-SA 4.0 |
| [CVDICT](https://github.com/ph0ngp/CVDICT) | Vietnamese meanings | CC BY-SA 4.0 |
| Thiều Chửu, *Hán Việt tự điển*, via [catusf/tudien](https://github.com/catusf/tudien) | Hán Việt readings | CC0 |
| [Unihan](https://www.unicode.org/charts/unihan.html) | Hán Việt where Thiều Chửu has none, strokes, variants | Unicode licence |
| [Make Me a Hanzi](https://github.com/skishore/makemeahanzi) | breakdown, radical, meaning and sound parts | LGPL-3.0 |
| [Complete HSK Vocabulary](https://github.com/drkameleon/complete-hsk-vocabulary) | HSK 2.0 and 3.0 levels | MIT |

Thank you to everyone who built and keeps these sources.

## Licence

The dataset is CC BY-SA 4.0, share-alike from CC-CEDICT and CVDICT. Credit "OpenCidian by Perxel" and the sources above. The code is MIT.

---

OpenCidian is made by [Perxel](https://perxel.com), a web tech studio in Vietnam.
