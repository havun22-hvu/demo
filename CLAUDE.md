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

## MD-docs schrijven — hou ze leesbaar voor Claude

Een te lang doc wordt niet gelezen: het verdringt andere docs uit de context, en de KB indexeert
alleen het **begin** van een bestand (~2000-8000 tekens) — alles daarna is onvindbaar via `docs:search`.

- **Max:** KB-doc/runbook 200 regels · CLAUDE.md 120 · plan/blueprint 300 · handover 15-30 regels per sessie
- **Hiërarchie:** conclusie + status bovenaan, tabel in het midden, onderbouwing onderaan
- **Te groot?** Splitsen in index + deeldocs. Niet persen tot telegramstijl — onleesbaar is niet kort
- **Handover:** nieuwste bovenaan; sessies ouder dan ~3 maanden weg (git bewaart de historie)

Volledig: `HavunCore/docs/kb/standards/md-doc-grootte.md`
