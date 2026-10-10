# Методология

1. Сформулировать проверяемый механический вопрос.
2. Проверить актуальные FAQ и Errata, затем Rulebook.
3. Присвоить статус по силе фактического источника.
4. Записать краткий итог, затем обоснование и точную ссылку.
5. Связать запись с моделями, бандами и темами.
6. Указать дату последней проверки и состояние `superseded`.

## Обязательные metadata

- `id` — уникален и не меняется при переименовании файла;
- `status` — `official`, `raw`, `community` или `disputed`;
- `source`, `version`, `reference` — позволяют найти основание;
- `topics` — используются для перекрёстных связей;
- `last_reviewed` — дата проверки в формате ISO;
- `superseded` — заменена ли запись более новой.

## Metadata исправлений карточек

Для записи с `kind: card_text_override` дополнительно используются:

- `cards` — список затронутых карточек;
- `element` — Ability, Action или Trigger;
- `errata_status` — `not_included` или `incorporated`;
- `errata_checked_version` — последняя проверенная Errata;
- `app_card_status` — состояние карточки в приложении;
- `player_action` — требуемое действие игрока.

## Политика состояния приложения

Если исправление вошло в официальную Errata, карточка в приложении по умолчанию считается актуальной:

```yaml
errata_status: incorporated
app_card_status: assumed_current
player_action: no_action
```

Если позднее будет подтверждено, что приложение всё ещё показывает старый текст, используется зарезервированный статус:

```yaml
errata_status: incorporated
app_card_status: confirmed_stale_after_errata
player_action: read_errata_instead
```

Исправление, ещё не включённое в Errata:

```yaml
errata_status: not_included
app_card_status: potentially_stale
player_action: read_faq_instead
```
