# OpenCidian

An open Chinese ↔ Vietnamese dictionary for AI assistants. Ask Claude, ChatGPT, Cursor or any MCP client about a Chinese word and it looks it up in OpenCidian instead of guessing: Hán Việt readings, pinyin, Vietnamese and English meanings, and how each character is built. Every value says which source it came from.

The name: 词典 *cídiǎn* and 詞典 *từ điển* are the same word, read in Mandarin and in Hán Việt.

## Use it

OpenCidian is a free MCP server, no sign-in:

```
https://opencidian-mcp.perxel.com/mcp
```

- **Claude** (claude.ai, Desktop, mobile): Settings → Connectors → Add custom connector → paste the URL.
- **Claude Code**: `claude mcp add --transport http opencidian https://opencidian-mcp.perxel.com/mcp`
- **ChatGPT**: Settings → Apps & Connectors → Advanced settings → turn on Developer mode → Create, then paste the URL (no authentication).
- **Cursor, VS Code** and other clients with an `mcp.json`:
  ```json
  { "mcpServers": { "opencidian": { "url": "https://opencidian-mcp.perxel.com/mcp" } } }
  ```
- **Clients that only speak stdio**: `npx mcp-remote https://opencidian-mcp.perxel.com/mcp`

Then ask, in Vietnamese or English:

- 觉得 nghĩa là gì? Âm Hán Việt là gì?
- "Cảm thấy" tiếng Trung nói thế nào?
- Chữ 觉 có những âm Hán Việt nào, gồm những bộ phận gì?
- Phiên âm và nghĩa từng từ trong câu: 他觉得北京很好。

| Tool | What it does |
|---|---|
| `lookup` | A word by hanzi, pinyin or Vietnamese: forms, pinyin, Hán Việt per character, Vietnamese and English meanings, HSK level |
| `get_character` | One character: Hán Việt, pinyin, radical, parts, meaning and sound parts, strokes, traditional form |
| `words_with` | Common words that contain a character |
| `search_meaning` | Vietnamese or English meaning → Chinese words |
| `annotate_text` | A Chinese text, word by word, with pinyin, Hán Việt and meaning |
| `suggest_correction` | Reports a wrong or missing value as a public issue for a maintainer to review |
| `about` | Dataset version, sources and how to cite |

The server is listed on the [MCP Registry](https://registry.modelcontextprotocol.io) as `io.github.OpenCidian/opencidian`. Full tool list: [opencidian-mcp.perxel.com](https://opencidian-mcp.perxel.com/), for AI: [llms.txt](https://opencidian-mcp.perxel.com/llms.txt).

## Why

There is no open dataset, public API or MCP server for Chinese → Vietnamese. The Vietnamese dictionary sites have no API, and the Chinese dictionary MCPs answer only in Chinese or English. OpenCidian puts the open sources together in one dataset of about 125,000 words and 14,500 characters, says where every value came from, and lets anyone suggest a fix.

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

Every character of a compound gets its Hán Việt readings, not only the first. A word the dictionary doesn't have is reported as missing, never guessed.

## Found a mistake?

Tell your assistant, with the dictionary or textbook that says otherwise, and it can file it through `suggest_correction`. Or [open an issue](https://github.com/OpenCidian/opencidian-data/issues/new) in `opencidian-data`. A maintainer reviews each one before the data changes.

## Repositories

| Repo | What it is |
|---|---|
| [`opencidian-mcp`](https://github.com/OpenCidian/opencidian-mcp) | The public MCP server, the only way in for apps and assistants |
| [`opencidian-data`](https://github.com/OpenCidian/opencidian-data) | The pinned sources, the community corrections, and the build that turns them into one dataset, published as GitHub releases |
| [`opencidian-api`](https://github.com/OpenCidian/opencidian-api) | The internal API behind the MCP server (Cloudflare Workers and D1) |

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
