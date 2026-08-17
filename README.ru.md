# 🧩 Velantrim AI Skills

> **Переиспользуемые, проектно-нейтральные AI-skills и role-guidance для аудита, анализа, implementation, adversarial review, verification, CI/governance, truth routing, воспроизводимости и bounded engineering workflows.**

🌍 Подходит для проектов Velantrim **и** сторонних software/research repositories.  
🔒 По умолчанию — read-only.  
🧭 Authority целевого проекта всегда выше generic role/skill guidance.  
🎭 Маршрутизатор ролей ИИ: [`roles/README.md`](roles/README.md)  
🤖 Вход для ИИ: [`docs/ai/README.md`](docs/ai/README.md)

---

## 👤 Сначала для человека — что это вообще?

`velantrim-ai-skills` — это внешний нейтральный набор инструментов для AI-агентов.

В нём два дополняющих друг друга слоя:

- 🎭 **roles** — определяют, за что ИИ отвечает на текущем этапе и что ему нельзя молча делать;
- 🧰 **skills** — дают переиспользуемую методику/checklists для конкретного вида работы.

Role или skill может помочь проверить, проанализировать, изменить, атаковать или верифицировать проект, но **не становится частью архитектуры целевого проекта и не наследует его authority**.

```text
                         🧩 Velantrim AI Skills
                                  │
                     нейтральный внешний tooling
                                  │
                 ┌────────────────┴────────────────┐
                 ▼                                 ▼
          🎭 КЕМ должен быть ИИ?             🧰 КАК ему работать?
                 roles/                             skills/
                    │                                  │
        ┌───────────┼───────────┐                     │
        ▼           ▼           ▼                     ▼
     🔍 Audit    🛠️ Build    🧨 Attack          reusable methodology
        │           │           │                     │
        └───────────┴─────┬─────┴─────────────────────┘
                          ▼
                  🧭 целевой проект
                          │
                          ▼
               authority остаётся у проекта
```

---

## 🎭 Роли ИИ — разделение ответственности

Когда ИИ получает задачу, он должен либо использовать роль, которую явно назначил пользователь, либо обратиться к [Role Router](roles/README.md).

```text
🔍 AUDITOR      → Что сейчас является фактом?
🧠 ANALYST      → Что означает собранное evidence?
🛠️ IMPLEMENTER  → Как выполнить разрешённое bounded изменение?
🧨 RED TEAM     → Как это может сломаться или быть обойдено?
🧪 VERIFIER     → Действительно ли заявленный результат доказан?
🧭 COORDINATOR  → Кто что должен делать и в каком порядке?
```

Главное разделение:

```text
найти проблему
      !=
доказать её root cause
      !=
написать исправление
      !=
независимо атаковать/проверить исправление
```

Для значимых изменений self-check автора полезен, но он не является independent verification. Для Red Team и Verifier предпочтителен другой actor/model/provider или хотя бы fresh isolated context, который самостоятельно перечитывает evidence.

➡️ [`roles/README.md`](roles/README.md)

---

## 🌳 Дерево репозитория

```text
🧩 velantrim-ai-skills/
├── 📖 README.md                    # human-first English entry
├── 📖 README.ru.md                 # human-first Russian entry
├── 🤖 AGENTS.md                    # общие AI boundaries
├── 🤖 docs/
│   └── ai/
│       └── README.md               # компактный AI-вход + routing
├── 🎭 roles/
│   ├── README.md                   # role router
│   ├── 🔍 auditor.md
│   ├── 🧠 analyst.md
│   ├── 🛠️ implementer.md
│   ├── 🧨 red-team.md
│   ├── 🧪 verifier.md
│   └── 🧭 coordinator.md
└── 🧰 skills/
    ├── README.md                   # каталог skills
    └── 🔍 github-notion-repository-audit/
        ├── SKILL.md                # canonical audit methodology
        ├── references/             # узкие checklists/guidance
        └── templates/              # report/finding/remediation templates
```

---

## 🔍 Первый reusable skill

### [`github-notion-repository-audit`](skills/github-notion-repository-audit/SKILL.md)

Универсальная evidence-based методика для аудита репозиториев, где operational truth может быть распределена между GitHub, Notion или другими documentation surfaces, CI, тестами, governance, кодом, reproducibility и supply-chain состоянием.

Он покрывает, когда это действительно относится к проекту:

- 🧭 live-first baseline и authority discovery;
- 🔐 branch/ruleset/merge-governance review;
- ⚙️ CI gate, false-pass и deadlock analysis;
- 🧪 поддерживаемые test paths и missing negative tests;
- 📚 GitHub ↔ Notion/documentation truth routing;
- 🔁 per-role freshness вместо одного global sync marker;
- 📦 dependency/reproducibility review;
- 🧯 declared limitation vs new defect;
- 🛠️ minimal remediation + Definition of Done;
- 🚦 recommendation/authorization boundaries.

Skill намеренно не содержит project-specific SHA, issue/PR numbers, experiment names, Notion page IDs, architecture vocabulary, обязательную reviewer policy, runtime, язык или БД.

---

## ⚡ Пример: быстрый multi-AI workflow

```text
              ┌── 🔍 code/GitHub audit ──┐
START ────────┼── 🔍 CI/governance ──────┼──► 🧠 ANALYST
              └── 🔍 docs/knowledge ──────┘         │
                                                     ▼
                                              👤 authority GO
                                                     │
                                                     ▼
                                              🛠️ IMPLEMENTER
                                                     │
                                          ┌──────────┴──────────┐
                                          ▼                     ▼
                                     🧨 RED TEAM            🧪 VERIFIER
                                          └──────────┬──────────┘
                                                     ▼
                                              🧭 reconcile
```

Read-only audit lanes можно выполнять параллельно. Implementation начинается только после reconciliation evidence и нужного authority. Red Team и independent verification не должны незаметно сливаться с authoring-session, когда независимость действительно важна.

---

## 🔒 Основные границы

```text
project-specific authority > generic role/skill defaults
read-only by default
role assignment != authority
IMPLEMENTER role != write permission
writes require explicit authorization
UNKNOWN stays UNKNOWN
recommendation != authorization
AUTHOR_SELF_CHECK != INDEPENDENT_VERIFICATION
CI success != production readiness
mirror/sync metadata != runtime evidence
ordinary review != specialized independent qualification
public repository != open-source license
```

Этот репозиторий **не является частью архитектуры** Native Kernel, Titan, Crystal, Mentaury, Continuum или любого другого целевого проекта. Эти названия — возможные пользователи tooling, а не authority relationship.

---

## 🤖 Для AI-агентов

Не восстанавливайте operating rules только из этого README.

Используйте такой reading order:

```text
1. AGENTS.md
2. docs/ai/README.md
3. roles/README.md
4. выбранный roles/<role>.md
5. skills/README.md              # если нужна reusable methodology
6. выбранный skill/SKILL.md
7. relevant references/templates
8. authority/governance docs самого целевого проекта
```

AI entry содержит компактную structured metadata и точное правило role routing.

➡️ [`docs/ai/README.md`](docs/ai/README.md)

---

## 📚 Authority model

Для **этого репозитория** GitHub является техническим источником истины для versioned role/skill content и истории.

Для **любого целевого проекта** roles и skills обязаны сначала обнаружить authority hierarchy самого проекта и не навязывать ему модель из Velantrim AI Skills.

Ни generic role, ни skill не могут повысить сами себя до authority целевого проекта.

---

## 🧠 Почему пока нет `project-state.json`?

Отдельный machine-state файл имеет смысл только если в репозитории появится реально меняющееся operational state, которое должна потреблять автоматизация.

Сейчас здесь в основном versioned methodologies и role guidance. JSON дублировал бы Markdown truth и создавал ещё одну поверхность drift. Поэтому AI-вход использует компактную structured YAML metadata внутри Markdown.

Если позже появится настоящий machine-state, лучше осознанно добавить versioned JSON schema, а не использовать JSON как декоративную копию README.

---

## ⚖️ Лицензия

Лицензия пока не выбрана. Публичная видимость репозитория сама по себе не даёт разрешения копировать, изменять, распространять или переиспользовать содержимое. Выбор лицензии остаётся решением владельца.