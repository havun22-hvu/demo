# End Session Command

Voer de volgende stappen uit om de sessie netjes af te ronden:

## ⛔ KRITIEKE GEDRAGSREGELS — ook hier geldig

### ✅ MD BEWERKEN = VOORAF GOEDGEKEURD — GEEN TOESTEMMING NODIG
Alle MD-bestanden (handover, context.md, KB-docs, smallwork.md) bewerken en committen is **automatisch toegestaan zonder enige bevestiging**.
Niet wachten op tool-bevestiging. Niet vragen. Niet pauzeren. Gewoon doen.
VERBODEN: "Mag ik de handover bijwerken?" / "Zal ik dit documenteren?" / elke vraag over MD-bewerking.

### Technische vragen = DOORPAKKEN
Commit-form, doc-structuur, wat te bewaren → Claude beslist zelf.

### Overleg = WACHTEN (geldt ook bij afsluitende discussies)
Nieuwe scope of features die opkomen bij /end → vermelden, NIET uitvoeren.

---


## 0. Handover bijwerken (EERST) (ALTIJD, EERST)

> **Er is één handover: `.claude/handover.md`. Die WERK JE BIJ — je plakt er nooit een sessie
> onderaan of bovenaan.** De handover is een **levende status** ("hoe staat dit project ervoor"),
> geen logboek ("wat deed ik wanneer"). Git bewaart de historie al; een tweede kopie in het doc
> maakt hem alleen onbetrouwbaar.
>
> **Ook niet in `context.md`.** Dat is projectkennis (architectuur, regels, valkuilen), geen
> tijdlijn. Een sessieverslag hoort daar net zomin. Levert een sessie een blijvend feit op
> (beslissing, valkuil, geverifieerde constatering)? → als kennis in de juiste sectie zetten,
> niet als "## Laatste Sessie: <datum>" eronder plakken.

Wat je bij elke `/end` doet:

1. **Afgeronde taken WEGHALEN.** Niet doorstrepen, niet naar "Afgerond" verplaatsen — weg.
   Klaar is klaar. Zit er waarde in voor later? → KB (`patterns/`, `runbooks/`, `decisions/`).
2. **Nieuwe open punten TOEVOEGEN** aan de bestaande lijst.
3. **Bestaande punten BIJWERKEN** als er iets veranderd is (status, oorzaak, volgende stap).
4. **Achterhaalde tekst SCHRAPPEN.** Klopt een ⚠️ of "wacht op deploy" niet meer? Weg ermee —
   verifieer het desnoods (`git log`, `composer.json`, server) in plaats van te laten staan.

Structuur van `.claude/handover.md` — hou het hierbij, geen extra sessie-koppen:

```markdown
---
title: <Project> Handover
last_updated: YYYY-MM-DD
---

# <Project> — Handover

**Branch:** <branch> · **Status:** <1 zin: draait het, wat is er gaande>

## Open — wacht op Henk
| Wat | Waar |
|-----|------|
| ... | ... |

## Open — te doen
- ...

## Recent afgerond (max ~10 regels, alleen wat de volgende sessie nog nodig heeft)
- ...

## Vaste context voor dit project
- ...
```

**Grootte:** max ~120 regels. Groeit hij daarboven, dan staat er te veel afgeronde geschiedenis in —
weghalen, niet splitsen. Regel: `HavunCore/docs/kb/standards/md-doc-grootte.md`.

**Waarom dit hard is:** JudoToernooi's handover groeide zo naar **842 regels** met 20+ sessieblokken,
waarin "(Afgerond) Laravel 12 — GEDEPLOYED" pal boven "⚠️ Laravel 12 — NOG NIET gedeployed" stond,
plus taken die al weken klaar waren. Zo'n doc kost context én liegt. Bovendien indexeert de KB alleen
het begin van een bestand — de onderkant van een lange handover is onvindbaar.

## 1. Update MD bestanden
- Update CLAUDE.md met relevante wijzigingen uit deze sessie
- Update CHANGELOG.md als er functionele wijzigingen zijn
- Check of andere docs bijgewerkt moeten worden

## 2. Git commit & push
- `git add .`
- Maak een duidelijke commit message met samenvatting van de wijzigingen
- `git push origin main`

## 3. Deploy naar server
- SSH naar 188.245.159.115
- Push naar staging remote voor auto-deploy:
  ```bash
  git push staging main
  ```

## 4. Branch cleanup
- Check op open branches: `git branch -a`
- Verwijder gemergte lokale branches: `git branch --merged | grep -v master | grep -v main | xargs git branch -d`
- Check open pull requests: `gh pr list`
- Sluit/merge open PRs indien gereed

## 5. Bevestig aan gebruiker
- Geef korte samenvatting van wat er gedaan is
- Vermeld eventuele openstaande items
- Staging URL: https://demo.havun.nl

## 6. Sluit Claude af
- Zeg: "Sessie afgerond. Druk Ctrl+D of typ 'exit' om Claude te sluiten."
