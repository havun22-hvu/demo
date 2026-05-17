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
