# findy KiCad Central Library

Споделени символи, footprint-и, 3D модели и шаблони за всички findy hardware проекти
(SOP-HW-000 §9). Включва се във всеки проектен repo като **git submodule** в `libs/central-lib`,
закачен (pinned) към фиксиран commit за всеки проект.

## Структура
```
/symbols/findy_central.kicad_sym        Споделени схематични символи
/footprints/findy_central.pretty/       Споделени footprint-и
/3d_models/                             STEP / WRL модели
/templates/                             Шаблони
/docs/                                  Документация на библиотеката
```

## Какво влиза тук vs. в проектната библиотека
| Централна (findy_central) | Проектна (findy_project) |
|---|---|
| Стандартни части: R, C, чести IC | Части само за един проект |
| Части в 2+ проекта | Частти с custom размери за един проект |
| Одобрени от HW Lead, с datasheet | Бързи добавки, без PR |

## Процес на добавяне (задължителен)
1. Инженер прави branch: `lib/add-<component>`
2. Добавя символ + footprint + 3D модел + връзка към datasheet
3. Отваря Pull Request
4. HW Lead преглежда и одобрява → merge в `main`
5. Проектите вземат новата версия при следващ `git submodule update --remote` (нарочно, per-project)

**Никога не трий и не променяй вече пусната част на място** — добави нова версия
(напр. `LM317_v2`) и миграционна бележка в `/docs/`. Съществуващите проекти трябва да продължат да се компилират.

## Използване в проект
```
git submodule add <URL-на-central-lib-repo> libs/central-lib
git submodule update --init --recursive
```
