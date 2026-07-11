# 🧠 TCE — Tarik Context Engineering

> **Преврати сырой запрос в идеальный промпт для AI-кодера за 3 шага.**

[![MIT License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Tarik Shehihar](https://img.shields.io/badge/method-Tarik%20Shehihar-blueviolet)](#-8-вопросов-тарика-шехипара)
[![Codex CLI](https://img.shields.io/badge/integration-Codex%20CLI-ff6600)](#-генерация-промпта-для-codex-cli)
[![NC777](https://img.shields.io/badge/pipeline-NC777%20v4-important)](#-nc777-ролевая-разметка)
[![Context Engineering](https://img.shields.io/badge/paradigm-Context%20Engineering-00bcd4)](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)

---

## 💥 The Problem

Ты даёшь AI-кодеру задачу. Получаешь **не то**. Докидываешь контекст — **чуть лучше**. Ещё 5 уточнений — **почти то**.

**Проблема не в AI. Проблема в контексте.**

Каждый токен в промпте — это бюджет. Плохой контекст = пустая трата лимита. Хороший контекст = результат с первой попытки.

**TCE** — это системный метод упаковки задачи в self-contained промпт, который понимает AI-кодер с первого раза. Без итераций. Без «ой, я забыл сказать».

---

## 🔬 Что внутри

TCE объединяет **4 компонента**:

| Компонент | Источник | Зачем |
|-----------|----------|-------|
| 🎯 **8 вопросов** | Тарик Шехипар | Вытащить из головы то, что вы забыли сказать |
| 🧱 **Context Engineering** | Phil Schmid / Google DeepMind + Anthropic | Упаковать в 5-слойную структуру |
| 🤖 **Codex CLI** | OpenAI | Исполнить с полным контекстом |
| 🔄 **NC777 Pipeline** | [NC 777 v4](https://github.com/NiiyazG/NC777) | Ролевая дисциплина: Prophet → Architect → Developer → QA → Cleaner |

---

## 📋 Workflow за 30 секунд

```
RAW REQUEST → 8 QUESTIONS → CONTEXT MAP → CODEX PROMPT
```

### Шаг 1 — 8 вопросов Тарика Шехипара

Система вопросов, которые вытаскивают **скрытые требования**:

| # | Вопрос | Раскрывает |
|---|--------|-----------|
| Q1 | **Какой конкретный результат?** | Что именно должно быть на выходе |
| Q2 | **Почему это важно?** | Мотивацию, боль, контекст проблемы |
| Q3 | **Как поймём, что готово?** | Критерии приёмки (checklist) |
| Q4 | **Как ты видишь архитектуру?** | Твои предпочтения, технологический стек |
| Q5 | **Первый минимальный шаг?** | MVP, с чего начать |
| Q6 | **Какие ресурсы нужны?** | Файлы, API, библиотеки, данные |
| Q7 | **Что может пойти не так?** | Риски, edge cases, узкие места |
| Q8 | **Какой контекст передать?** | Background, ссылки, спецификации |

> **Правило:** задаём только то, на что ещё нет ответа. Если сказал «сделай сам» — не спрашиваем, используем дефолты.

### Шаг 2 — Контекстный инжиниринг (5-Layer Stack)

По мотивам [Phil Schmid / Google DeepMind](https://www.taskade.com/blog/context-engineering) и [Anthropic](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents):

```
┌─ Layer 1: System Prompt ─────────────────────────┐
│  Ты — senior Python-разработчик.                 │
│  Используешь pep8, typing, pytest.               │
│  Не используешь сторонние БД без необходимости.   │
├─ Layer 2: Memory / State ────────────────────────┤
│  Проект: парсер Excel→JSON. openpyxl. 340 строк. │
├─ Layer 3: Retrieval / Context ───────────────────┤
│  src/parser.py, tests/test_parser.py             │
├─ Layer 4: Tools & APIs ──────────────────────────┤
│  ✅ openpyxl, pathlib, re  ❌ pandas, numpy       │
├─ Layer 5: Output Format ─────────────────────────┤
│  1. Модифицировать src/parser.py                 │
│  2. Обновить тесты                               │
│  3. Вывести diff                                  │
└──────────────────────────────────────────────────┘
```

### Шаг 3 — Генерация промпта для Codex CLI

```bash
ALL_PROXY=socks5h://127.0.0.1:10808 codex exec \
  -m gpt-5.3-codex \
  -s danger-full-access \
  -c skip_git_repo_check=true \
  --dangerously-bypass-approvals-and-sandbox \
  "$(cat prompt.md)"
```

---

## 🧩 Библиотека методик (все в одном)

TCE не ограничивается Тариком. Встроена подборка лучших методик:

| Методика | Когда использовать | Совместимость |
|----------|-------------------|---------------|
| **8Q Тарика Шехипара** | Размытая фича, новый проект | 🔟 базовая |
| **GROW** (Whitmore) | Быстрое действие, первый шаг | ➕ Q1→G, Q7→R, Q4→O, Q5→W |
| **5-Layer Context Stack** | Сложные AI-системы | 🧱 архитектура контекста |
| **Anthropic Context Engineering** | Production-промпты | 💰 Context Budgeting |
| **SMART** | Критерии приёмки | ✅ проверка достижимости |
| **5W2H** | Быстрая постановка | 📋 What/Why/Where/When/Who/How/How much |
| **SCQA** (Minto) | Баги и проблемные сценарии | 🐛 Situation → Complication → Question → Answer |

Подробнее — в [SKILL.md](SKILL.md#библиотека-методик).

---

## 🔄 NC777 — Ролевая разметка

Для каждой задачи TCE проставляет роли NC777 —Operating System для AI-агентов:

| Сложность | Конвейер | Пример |
|-----------|----------|--------|
| 🟢 Простая | Developer → QA | Один файл, < 50 строк |
| 🟡 Средняя | Prophet → Architect → Developer → QA → Cleaner | 2–5 файлов |
| 🔴 Сложная | Prophet → Architect → Reviewer → Developer → QA → Saboteur → Cleaner | Архитектурные изменения |

Про NC777 — [NiiyazG/NC777](https://github.com/NiiyazG/NC777).

---

## 🚀 Быстрый старт (как использовать)

TCE — это **метод**, не библиотека. Чтобы применить:

```bash
# 1. Скачай промпт файл как шпаргалку
wget -O tce-prompt.md https://raw.githubusercontent.com/NiiyazG/tce/main/SKILL.md

# 2. Пройди 8 вопросов (в голове или с командой)

# 3. Собери Context Map по 5-слойной схеме

# 4. Склей в промпт и отправь в Codex CLI
```

Или просто попроси **любого AI-агента** (включая этого) применить TCE к твоей задаче — навык уже встроен.

---

## 📚 Структура репозитория

```
tce/
├── README.md           ← этот файл
├── SKILL.md            ← полная спецификация метода
├── LICENSE             ← MIT
└── references/
    └── methodology-comparison.md  ← детальное сравнение методик
```

---

## 🧠 Почему это работает

1. **Вопросы Тарика** вытаскивают скрытые требования, которые вы даже не осознавали
2. **5-Layer Stack** распределяет информацию по слоям — AI не путается
3. **NC777 Pipeline** добавляет ролевую дисциплину — каждая стадия делает своё
4. **Context Budgeting** экономит токены — AI не захлёбывается в мусоре

> «Контекстный инжиниринг — навык, определяющий AI-разработку 2026 года» — Phil Schmid, Google DeepMind

---

## 📄 Лицензия

MIT © [Niyaz Garipov](https://github.com/NiiyazG)

---

## 🌐 Ссылки

- [Anthropic: Effective Context Engineering for AI Agents](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents)
- [Taskade: Context Engineering Field Guide 2026](https://www.taskade.com/blog/context-engineering)
- [Awesome Context Engineering](https://github.com/Meirtz/Awesome-Context-Engineering)
- [NC 777 — Role Operating System for AI Agents](https://github.com/NiiyazG/NC777)
