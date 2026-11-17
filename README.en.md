# EH-Poem-Style

**English** | [中文](README.md)

![CI](https://github.com/ChenyangZhao7/eh-poem-style/actions/workflows/ci.yml/badge.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

Generate classical Chinese poetry — ancient-style verse, regulated verse (lüshi), quatrains (jueju), and ci — using 56 of your own poems as the style sample.

- Shi: uses Zhonghua Xinyun; validates rhyme and line/character counts only, not tonal patterns.
- Ci: strictly validates tones, pauses, rhyme positions and rhyme groups against cipai templates (Zhonghua Xinyun).
- Swappable models: DeepSeek V4.1 and local Ollama (default `qwen3.5:4b`) can be compared on the same prompt.
- Every generation, retry and manual edit is persisted, so the corpus keeps growing.

## Quick start

```powershell
python -m pip install -e ".[dev]"
Copy-Item config.example.toml config.toml
$env:DEEPSEEK_API_KEY = "your key"
python -m pytest -q
python -m eh_poem_style --help
```

## Corpus and few-shot

- `corpus/seed/seed.md`: the user's original 56 poems, read-only.
- `style/fewshot.txt`: 10 selected poems used in the prompt; the rest only feed statistics and future fine-tuning.
- `corpus/drafts/`: AI-generated or AI-assisted drafts (`status: draft`), excluded from few-shot.
- `corpus/poems/`: user-approved final poems (`status: final`).

Design and plan:

- Design: `docs/superpowers/specs/2026-11-06-eh-poem-style-design.md`
- Plan: `docs/superpowers/plans/2026-11-06-eh-poem-style.md`

`demo.py` is an early vertical-slice demo; the `eh_poem_style` package is the canonical implementation.
