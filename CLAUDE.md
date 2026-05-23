# Demo — Claude Instructions

> **Type:** Schone demo-omgeving voor nieuwe klantprojecten
> **URL:** https://demo.havun.nl
> **Server:** 188.245.159.115 — `/var/www/demo/production`
> **KB zoeken:** `cd D:/GitHub/HavunCore && php artisan docs:search "<onderwerp>"`

## Kritieke Gedragsregels

| Situatie | Wat Claude doet |
|----------|----------------|
| **Overleg/discussie** | Luisteren, samenvatten + plan — code pas na "ga maar" |
| **Technische beslissing** | Zelf beslissen, kort melden wat er gedaan is |
| **MD bijwerken** | Gewoon doen — nooit toestemming vragen |

## Verboden zonder overleg

- `.env` aanpassen
- Nieuwe dependencies installeren
- Database migrations op production
- SSH keys of credentials wijzigen

## AI Werkwijze — Gemini + Claude

- **`/arch [opdracht]`** — Gemini blauwdruk genereren (groot contextvenster)
- **`/mpc ga maar`** — blauwdruk uitvoeren
- Blauwdruk landt in `.claude/blueprint.md`, `/start` detecteert dit automatisch

Zie `docs/kb/runbooks/gemini-claude-workflow.md` voor de volledige pipeline.
