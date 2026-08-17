# 🧩 Velantrim AI Skills

Нейтральная коллекция переиспользуемых AI-навыков для аудита репозиториев, проверки CI и governance, маршрутизации истины GitHub ↔ Notion, воспроизводимости, валидации evidence, качества документации, анализа рисков и инженерных рабочих процессов.

## 🎯 Назначение

Этот репозиторий — внешний нейтральный tooling-слой. Skills из него могут проверять и помогать другим проектам, но **не становятся частью архитектуры этих проектов** и **не наследуют их authority**.

Репозиторий рассчитан как на проекты Velantrim, так и на другие software/research repositories, где полезны повторяемые evidence-based AI workflows.

## 🧭 Границы

Этот репозиторий **не является частью архитектуры**:

- Velantrim Native Kernel;
- Velantrim Titan;
- Velantrim Exo-Cortex Crystal;
- Mentaury Soul;
- Mentaury Kernel;
- Velantrim Continuum;
- или любого другого проекта, который проверяется skill-ом.

Skill может читать исходный код, документацию, тесты, CI, governance и связанные knowledge surfaces целевого проекта, если это разрешено. Правила самого целевого проекта всегда имеют приоритет.

## 🔒 Режим по умолчанию

```text
project-specific authority > generic skill defaults
read-only by default
writes require explicit authorization
unknown state stays UNKNOWN
recommendation ≠ authorization
CI success ≠ production readiness
sync metadata ≠ runtime evidence
```

Skills не должны молча изменять репозитории, внешние системы, governance-настройки, issues, pull requests или документацию только потому, что исправление кажется очевидным.

## 🧰 Структура

```text
velantrim-ai-skills/
├── README.md
├── README.ru.md
├── AGENTS.md
└── skills/
    └── README.md
```

Каждый переиспользуемый skill размещается в `skills/<skill-name>/`.

Первым планируется нейтральный skill для глубокого аудита GitHub + Notion. Его реализация намеренно не включена в bootstrap-коммит: она будет добавлена отдельно после проверки нейтральности методики.

## 📚 Authority

Для самого `velantrim-ai-skills` техническим источником истины является GitHub и его versioned history.

При аудите другого проекта skill обязан сначала обнаружить authority hierarchy этого проекта, а не навязывать ему модель из Velantrim AI Skills.

## ⚖️ Лицензия

Лицензия пока не выбрана. Публичная видимость репозитория сама по себе не даёт разрешения копировать, изменять, распространять или переиспользовать содержимое. Выбор лицензии остаётся решением владельца.
