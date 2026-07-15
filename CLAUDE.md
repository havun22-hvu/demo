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

## ⛔ Docs-first — code zonder MD is geen code

**Ga je implementeren? Werk EERST de MD bij (docs en/of plan), dan pas code. Andersom nooit.**

- **Groot** (feature, architectuur, >5 bestanden) → volledige `/mpc`: docs → plan → wacht op "ga maar" → code
- **Middel** (~2-5 bestanden) → plan-MD + de feature-doc die het raakt, dan bouwen
- **Klein** (bugfix) → de doc die het gedrag beschrijft + het punt in de handover, dan fixen
- **Triviaal** (typo, formatting) → enige uitzondering, geen MD nodig

Wijkt de implementatie af van het plan? **Eerst de MD bijwerken, dan verder.** Nooit stilzwijgend.
De omvang bepaalt hoevéél MD, niet óf. MD's bijwerken mag altijd zonder overleg.

Volledig: `HavunCore/docs/kb/standards/docs-first.md`

## MD-docs schrijven — hou ze leesbaar voor Claude

Een te lang doc wordt niet gelezen: het verdringt andere docs uit de context, en de KB indexeert
alleen het **begin** van een bestand (~2000-8000 tekens) — alles daarna is onvindbaar via `docs:search`.

- **Max:** KB-doc/runbook 200 regels · CLAUDE.md 120 · plan/blueprint 300 · handover 15-30 regels per sessie
- **Hiërarchie:** conclusie + status bovenaan, tabel in het midden, onderbouwing onderaan
- **Te groot?** Splitsen in index + deeldocs. Niet persen tot telegramstijl — onleesbaar is niet kort
- **Handover:** er is er **één** en die werk je **bij** — nooit een sessieblok toevoegen.
  Afgeronde taken eruit, nieuwe erbij. Levende status, geen logboek (git bewaart de historie)

Volledig: `HavunCore/docs/kb/standards/md-doc-grootte.md`
