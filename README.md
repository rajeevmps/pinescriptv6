# Pine Script® v6 Reference for LLMs

**Version:** Pine Script v6 · **Docs retrieved:** 2026-08-20

The complete official [Pine Script® v6 User Manual](https://www.tradingview.com/pine-script-docs/welcome/)
— all 77 pages — converted to clean Markdown, plus the
[v6 API reference dictionary](https://www.tradingview.com/pine-script-reference/v6/),
split into namespaced files.

## 🤖 Why this exists

The official documentation is large and lives behind a JavaScript-rendered site.
Pasting all of it into an LLM blows the context window and tends to produce
hallucinated or v5-flavoured code. This repository breaks it into logical,
namespaced Markdown files so a model can retrieve exactly the page it needs —
better RAG, smaller context, fewer invented functions.

Every file records its source URL and retrieval date in an HTML comment at the top,
so you can always check a page against the original.

---

## 📂 What's here

```
welcome.md                     Overview of Pine Script v6
primer/            3 pages     First steps, first indicator, next steps
language/         17 pages     Execution model, types, control flow, arrays, maps, objects
visuals/          11 pages     plot(), fills, lines, boxes, labels, tables
concepts/         13 pages     Alerts, inputs, strategies, sessions, repainting, MTF data
writing/           5 pages     Style guide, debugging, profiling, publishing, limitations
errors/            6 pages     Error-code explanations
faq/              13 pages     Task-shaped recipes from TradingView
migration-guides/  6 pages     v5 → v6 and older migrations
release-notes.md               Full version history
reference/        13 files     The API dictionary — 884 entries
LLM_MANIFEST.md                The map. Start here.
```

---

## 👨‍💻 For humans

### AI code editors (Cursor, Windsurf, Copilot)

Clone the repo and reference files by path in chat:

- Building an indicator? `@reference/functions/ta.md` and `@visuals/plots.md`
- Building a strategy? `@concepts/strategies.md` and `@reference/functions/strategy.md`
- Hitting an error? `@errors/overview.md`
- Converting a v5 script? `@migration-guides/to-pine-version-6.md`

### Claude Projects / Custom GPTs

Download the repo as a ZIP and upload the folders you use most to
[Claude Project knowledge](https://support.claude.com/en/articles/9517075-what-are-projects)
or Custom GPT knowledge. Always include `LLM_MANIFEST.md` — it is the routing table.

### Claude Code

Point at the repo and let the model read files on demand; `LLM_MANIFEST.md`
tells it which page answers which kind of question.

---

## 🧠 For LLMs

**If you are an AI assistant reading this file:**

1. **Entry point:** read [`LLM_MANIFEST.md`](LLM_MANIFEST.md) first. It maps intent → file.
2. **Retrieve narrowly.** Do not ingest the whole repository. One or two files
   answer almost every question.
3. **Two kinds of source, used differently:**
   - Top-level folders are the **User Manual** — narrative explanations, worked
     examples, and the reasoning behind a feature.
   - [`reference/`](reference/README.md) is the **dictionary** — look up an exact
     identifier's behaviour, return value, and example.
4. **Always emit `//@version=6`.**
5. **No invented syntax.** If an identifier is not in `reference/`, it very likely
   does not exist in v6 or was renamed — check
   [`migration-guides/to-pine-version-6.md`](migration-guides/to-pine-version-6.md).
   Note the [known reference gaps](reference/README.md#known-gaps) before concluding
   something is missing.

---

## 📋 Recommended system prompt

> You are an expert Pine Script v6 developer with access to a structured reference library.
>
> 1. Consult `LLM_MANIFEST.md` to locate the right file before writing code.
> 2. Every script starts with `//@version=6`.
> 3. Prefer `ta.*` built-ins over hand-rolled calculations.
> 4. For strategies, check `concepts/strategies.md` for order semantics and
>    `reference/functions/strategy.md` for exact call syntax.
> 5. For drawings, check `visuals/lines-and-boxes.md` and `visuals/text-and-shapes.md`;
>    respect the object limits documented in `writing/limitations.md`.
> 6. Never invent a built-in. If it is not in `reference/`, say so.

---

## 🔄 Keeping this current

TradingView ships Pine updates regularly — check
[`release-notes.md`](release-notes.md) against the
[live release notes](https://www.tradingview.com/pine-script-docs/release-notes/)
to see whether this snapshot has fallen behind.

---

*Community-maintained restructuring of the official documentation for AI use.
Not affiliated with TradingView. All documentation content is © TradingView.*
