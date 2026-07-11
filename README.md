# TCE — Tarik Context Engineering

**RU:** Уточнение задачи через 8 вопросов Тарика Шехипара + контекстный инжиниринг + генерация промпта для Codex CLI / Claude Code / Hermes с ролевой моделью NC777. Превращает сырой запрос в self-contained промпт с разметкой контекста.

**EN:** Task refinement via Tarik Shehipar's 8 questions + context engineering + prompt generation for Codex CLI / Claude Code / Hermes with NC777 role model. Transforms raw requests into self-contained prompts with full context markup.

## Методология / Methodology

Основано на **8 вопросах Тарика Шехипара** для уточнения задач (Tarik Shehipar's 8-Question Framework) и **Context Engineering** — методологии подготовки контекста для AI-агентов.

Методология: https://github.com/NiiyazG/tce

## Установка / Installation

```bash
# OpenClaw
cp -r tce ~/.openclaw/workspace/skills/
# Codex / Claude Code
cp -r tce /path/to/agent/skills/
```

## Структура / Structure

```
tce/
├── SKILL.md                        — полное описание методологии
├── README.md                       — этот файл
└── references/
    └── methodology-comparison.md   — сравнение подходов
```

## Триггеры / Triggers

- Русский: уточни задачу, контекстный инжиниринг, сделай промпт для кодекса, тарик, tce
- English: tce, tarik, 8 questions, context engineering, prepare task for codex
