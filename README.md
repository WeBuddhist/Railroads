# Railroads

**Laying the Tracks for Text Transformation Grounded in Tradition.**

Railroad is a structured, open reference system for classical Buddhist texts. Instead of asking AI models to interpret ancient texts from scratch every time, Railroad pre-resolves all the hard interpretive questions — word by word, verse by verse — using the classical commentary tradition. The result is a set of **context packages** that any AI model can use to produce reliable translations, lessons, or adaptations without redoing the philological work.

## Why This Exists

LLMs are bad at translating classical Buddhist texts reliably. Not because they lack knowledge, but because these texts are deeply ambiguous — a single Sanskrit compound can have multiple valid readings, and only the commentary tradition tells you which one applies. Feeding raw commentaries into a chat session doesn't solve this: the context is too large, too unstructured, and every translation starts from zero.

Railroad fixes this by doing the interpretive work once and storing it in a structured, reusable format.

## How It Works

For each verse or passage, a **context package** is compiled containing:

- **Source text** — original language with transliteration
- **Morphological analysis** — every word tagged with lemma, part of speech, and compound breakdown
- **Syntactic tree** — sentence structure following the commentarial reading
- **Semantic glosses** — the active meaning of each term (and which meanings are excluded)
- **Interpretive notes** — what each commentary says is happening, with citations

Every field traces back to a specific commentary passage. When commentaries disagree, the disagreement is recorded explicitly — never flattened.

## Project Structure

```
Railroad/
├── 0_Project/                 ← project docs and guidelines
├── 1_Human_Sources/           ← ground truth texts (read-only for AI)
├── 2_Authoritative_Context/   ← structured context packages (AI-compiled)
├── 3_Text_Transformations/    ← generated translations, lessons, etc.
└── 4_Wiki/                    ← cross-text concept knowledge
```

**Citation chain:** `1_Human_Sources → 2_Authoritative_Context → 3_Text_Transformations / 4_Wiki`. No link can be skipped. Every AI-generated claim is traceable back to a human source.

## Current Texts

| Text | Language | Period | Scope |
|------|----------|--------|-------|
| **Bodhicaryavatara** (BCA) | Sanskrit | 8th c. | ~900 verses on the bodhisattva path |
| **Abhidhamma Pitaka** | Pali | Canonical | Seven treatises of systematic analysis |

## Contributing

Two roles are needed:

- **Domain Specialists** — scholars who evaluate and correct the AI-generated analysis against the commentary tradition. No coding required.
- **AI Skills Designers** — contributors who build prompts, lint passes, and workflows. No Sanskrit/Pali required.

Start with `0_Project/README.md` for full onboarding details, and `CLAUDE.md` for the schema the AI works from.

## What Railroad Is Not

- Not an AI model — it's the **track**, not the engine
- Not a translation archive — outputs are grounded in tradition but are not scholarly editions
- Not finished — coverage is incremental; only `status: complete` fields are fully reviewed
