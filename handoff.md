# Handoff — Flex-Pool, 2026-11-18

## Nachtrag 2026-11-18 (1) — Genesis-Registrierung + Deploy + grimmige Analyse
- **[ERLEDIGT]:** Repo `Renekrieg1401/Flex-Pool` geklont nach
  `Projekte/Flex-Pool/`, `CLAUDE.md`+`handoff.md` angelegt, in Root-
  `CLAUDE.md` registriert.
- **[ERLEDIGT] Deploy:** `/var/www/flex-pool/` auf dem vServer, nginx-
  Backup vor Änderung (`aeris.bak-<timestamp>-flexpooladd`), neue
  `location /flex-pool/` NUR im 443-Serverblock, bewusst OHNE
  `auth_basic off` (Dokument enthält reale Lohn-/Finanzdaten eines echten
  Arbeitgebers — erbt die bestehende AERIS-Basic-Auth). Live-Check: HTTPS
  ohne Credentials → 401 (korrekt gesperrt), Port 80 → nur allgemeiner
  Redirect, kein eigener Eintrag dort.
- **[ERLEDIGT] Technische Analyse:** Playwright-Lauf — 0 Konsolenfehler,
  kein horizontaler Overflow (Desktop 1280px + Mobile 390px geprüft),
  responsive Breakpoints (Timeline/Tabelle/Spalten) funktionieren korrekt.
  Reines HTML/CSS, kein JavaScript — als "Präsentation" betitelt, aber ohne
  jede Navigation (kein Vor/Zurück, kein Vollbild, kein Druck-Layout) — nur
  eine lange Scroll-Seite mit 13 als "Folie" gestylten Divs.
- **[ERLEDIGT] Inhaltliche Funde (grimmig, Details s. Chat-Antwort):**
  2 Tippfehler (`index.html:503` "Stammmitarbeiterers", `index.html:611`
  "gesteuer" statt "gesteuert"). Finanzmodell-Mathematik selbst ist
  rechnerisch korrekt (alle Summen in der Tabelle geprüft), aber auf einer
  fragilen/zirkulären Prämisse aufgebaut: Zielüberschuss von nur +20€/Jahr,
  Kernerlös aus den extrahierten (oft aufwändigeren) Klienten wird bewusst
  mit 0€ "neutral deklariert" statt real verbucht, Break-Even hängt
  komplett an einer fest vorgegebenen Zahl von §37.3-SGB-XI-Beratungen
  (786/854/815), deren tatsächliche Marktverfügbarkeit (wie viele
  anspruchsberechtigte Angehörige/Pflegebedürftige gibt es in den 5
  Bezirken wirklich) nirgends im Dokument belegt wird — die Zahl wird
  rückwärts aus dem gewünschten Ergebnis hergeleitet, nicht aus echter
  Nachfrage. Risikofolie nennt selbst "fehlende valide Datenbasis" als
  Risiko, während die Finanzfolie exakte Euro-Beträge darauf aufbaut —
  innerer Widerspruch im selben Dokument.
- **[OFFEN]:** Keine Primärquellen-Prüfung von § 37.3 SGB XI (Beratungs-
  einsatz-Pauschale, Anspruchsvoraussetzungen) oder der KDO-Entgeltgruppe
  E7/Stufe 3 durchgeführt — keine `legal-compliance`-Agentenfreigabe
  angefordert, reine Logik-/Code-Analyse. Keine inhaltlichen Korrekturen
  vorgenommen (René hat nur Analyse + Feedback angefordert, keinen Fix).
## Nachtrag 2026-11-18 (2) — Agentenkette "wasserdicht machen" (René-Freigabe)
- **[ERLEDIGT] Strikt sequenzielle Kette:** `legal-compliance` →
  `business-consultant` → `business-finance` → Claude (Implementierung) →
  `business-consultant` (Gegenprüfung, geschlossener Regelkreis).
- **[ERLEDIGT] legal-compliance-Fund:** Der angesetzte 70,00-€-
  Beratungssatz (§37.3 SGB XI) war nicht nur unbelegt, sondern lag 5 €
  UNTER dem real verhandelten Hessen-Satz (75,00 €, vdek-
  Leistungsbeschreibung Hessen, inkl. Hausbesuchspauschale). Die
  786/854/815-Beratungen waren im Dokument als frei wählbare Stellschraube
  dargestellt, sind aber gesetzlich auf 2-4 Beratungen/Klient/Jahr gedeckelt
  (§ 37 Abs. 3 SGB XI) — entspricht ca. 200-400 real abrufenden Klienten in
  den 5 Bezirken. KDO/EKHN/E7-Stufe-3 bestätigt korrekt und plausibel.
- **[ERLEDIGT] business-consultant-Fund (1. Lauf):** 4 KRITISCH (K1-K4) + 2
  WICHTIG (W1-W2) — Dokument war "nicht vorstandsreif".
- **[ERLEDIGT] business-finance:** lieferte konkrete Textbausteine/Zahlen
  für alle 6 Punkte (Puffer-Empfehlung +5.000€/≈3,3%, Disclaimer-Text,
  Szenario-D-Berechnung, Risiko-Ergänzung, K1-Platzhalter-Formulierung).
- **[ERLEDIGT] Implementierung (Claude):** Satz 70€→75€ korrigiert, Ziel-
  Ergebnis +20€→+5.000€ angehoben, neue Szenario-D-Spalte (Worst-Case,
  -15% Abrufquote) ergänzt, K1-"0,00€/neutral"-Formulierung durch ehrliche
  "nicht quantifiziert"-Formulierung ersetzt, K3-Disclaimer-Absatz ergänzt,
  W2-Risiko (Single-Point-of-Failure der Reserve selbst) in Risikoliste
  ergänzt, 2 Tippfehler behoben. Alle Tabellenwerte neu durchgerechnet und
  intern konsistent (Playwright: 0 Fehler, kein Overflow). Deployed (MD5-
  identisch bestätigt), committed+gepusht (`41e7dec`).
- **[ERLEDIGT] Geschlossener Regelkreis (2. business-consultant-Lauf,
  eigenständig gegen den echten Code, nicht gegen meinen Bericht):** K1 ✅,
  K2 ✅, K3 ✅, W1 ✅ sauber behoben (inkl. eigener Nachrechnung). K4 (reale
  Klientenzahl) und W2 (konkrete Gegenmaßnahme für Reserve-Ausfall) nur
  ⚠️ teilweise — beide jetzt aber ehrlich als offen deklariert statt
  verschleiert. Verdikt: "kein KRITISCH mehr im Sinne von Täuschung/
  Rechenfehler, aber nicht entscheidungsreif ohne Vorbehalt."
- **[OFFEN, bewusst nicht durch einen Agenten lösbar]:** K4 (echte
  Bestandszahl der §37.3-anspruchsberechtigten Klienten in den 5 Bezirken)
  und W2 (konkrete Backup-Maßnahme bei Ausfall einer Flex-Pool-Kraft
  selbst) brauchen reale Betriebsdaten/Personalplanung bei René/Diakonie
  Gladenbach — liegt außerhalb dessen, was aus dem Repo heraus verifizierbar
  ist.
