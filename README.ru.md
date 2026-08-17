# 🧩 Velantrim AI Skills

> **Переиспользуемые, проектно-нейтральные AI-skills для глубокого аудита репозиториев, проверки CI/governance, маршрутизации истины, воспроизводимости, evidence validation, качества документации, анализа рисков и bounded engineering workflows.**

🌍 Подходит для проектов Velantrim **и** сторонних software/research repositories.  
🔒 По умолчанию работает в read-only режиме.  
🧭 Правила и authority целевого проекта всегда выше generic skill guidance.  
🤖 Вход для ИИ: [`docs/ai/README.md`](docs/ai/README.md)

---

## 👤 Сначала для человека — что это вообще?

`velantrim-ai-skills` — это внешний нейтральный репозиторий с переиспользуемыми процедурами для AI-агентов.

Skill из этого репозитория может проверить проект, структурировать аудит, сопоставить GitHub с Notion/документацией, найти риски CI или governance и предложить ограниченное исправление. Но он **не становится частью архитектуры проверяемого проекта** и **не наследует его authority**.

Проще всего представить это как внешний набор инструментов:

```text
                     🧩 Velantrim AI Skills
                              │
                    нейтральный tooling-слой
                              │
          ┌───────────────────┼───────────────────┐
          ▼                   ▼                   ▼
     🔍 Audit skills      ⚙️ CI/governance    📚 Truth routing
          │                   │                   │
          └───────────────────┼───────────────────┘
                              ▼
                    🧭 Проверка целевого проекта
                              │
                              ▼
                   authority остаётся у проекта
```

---

## 🌳 Дерево репозитория

```text
🧩 velantrim-ai-skills/
├── 📖 README.md                    # human-first English entry
├── 📖 README.ru.md                 # human-first Russian entry
├── 🤖 AGENTS.md                    # общие границы работы AI
├── 🤖 docs/
│   └── ai/
│       └── README.md               # компактный AI-вход + reading order
└── 🧰 skills/
    ├── README.md                   # каталог/вход к skills
    └── 🔍 github-notion-repository-audit/
        ├── SKILL.md                # canonical audit methodology
        ├── references/             # узкие checklists/guidance
        └── templates/              # шаблоны отчётов/findings/remediation
```

---

## 🔍 Первый reusable skill

### [`github-notion-repository-audit`](skills/github-notion-repository-audit/SKILL.md)

Универсальная evidence-based методика для аудита репозиториев, где operational truth может быть распределена между GitHub, Notion или другими documentation surfaces, CI, тестами, governance, исходным кодом, reproducibility и supply-chain состоянием.

Он покрывает, когда это действительно относится к проекту:

- 🧭 live-first baseline и authority discovery;
- 🔐 branch/ruleset/merge-governance review;
- ⚙️ CI gate и deadlock analysis;
- 🧪 поддерживаемые тестовые пути и missing negative tests;
- 📚 GitHub ↔ Notion/documentation truth routing;
- 🔁 per-role freshness вместо одного вводящего в заблуждение global sync marker;
- 📦 dependency/reproducibility review;
- 🧯 отличие declared limitation от нового дефекта;
- 🛠️ minimal remediation + Definition of Done;
- 🚦 явную границу между recommendation и authorization.

Skill намеренно не содержит project-specific SHA, issue/PR numbers, experiment names, Notion page IDs, architecture vocabulary, обязательную reviewer policy, конкретный runtime, язык или БД.

---

## 🔒 Основные границы

```text
project-specific authority  >  generic skill defaults
read-only by default
writes require explicit authorization
UNKNOWN stays UNKNOWN
recommendation != authorization
CI success != production readiness
mirror/sync metadata != runtime evidence
ordinary review != specialized independent qualification
public repository != open-source license
```

Skills не должны молча изменять репозитории, внешние системы, rulesets, issues, pull requests, CI, releases или документацию только потому, что исправление выглядит очевидным.

Этот репозиторий **не является частью архитектуры** Native Kernel, Titan, Crystal, Mentaury, Continuum или любого другого проверяемого проекта. Эти названия — только примеры возможных пользователей tooling, а не связь authority.

---

## 🤖 Для AI-агентов

Не нужно восстанавливать правила работы только из этого README.

Используйте такой reading order:

```text
1. AGENTS.md
2. docs/ai/README.md
3. skills/README.md
4. выбранный skill/SKILL.md
5. выбранный skill/references/* по необходимости
6. выбранный skill/templates/* при формировании результата
7. собственные authority/governance docs целевого проекта
```

Отдельный AI-вход содержит компактную структурированную сводку и объясняет, где заканчивается generic guidance и начинаются правила целевого проекта.

➡️ [`docs/ai/README.md`](docs/ai/README.md)

---

## 📚 Authority model

Для **этого репозитория** GitHub является техническим источником истины для versioned skill content и истории.

Для **любого проверяемого репозитория** skill обязан сначала обнаружить authority hierarchy самого проекта и не навязывать ему модель из Velantrim AI Skills.

Generic skill не может повысить сам себя до authority целевого проекта.

---

## 🧠 Почему пока нет `project-state.json`?

Отдельный machine-state файл имеет смысл только тогда, когда в репозитории появляется реально меняющееся operational state, которое должна потреблять автоматизация.

Сейчас здесь в основном versioned methodologies. JSON-файл дублировал бы Markdown truth и создавал дополнительную поверхность drift. Поэтому AI-вход использует компактную structured metadata прямо внутри Markdown.

Если позже появится настоящий machine-state, лучше осознанно добавить versioned JSON schema, а не использовать JSON как декоративную копию README.

---

## ⚖️ Лицензия

Лицензия пока не выбрана. Публичная видимость репозитория сама по себе не даёт разрешения копировать, изменять, распространять или переиспользовать содержимое. Выбор лицензии остаётся решением владельца.
