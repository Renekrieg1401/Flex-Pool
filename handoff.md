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
- **[KORREKTUR-POTENZIAL]:** Falls René das Dokument tatsächlich dem
  Vorstand vorlegen will: die beiden Tippfehler sowie die Extraktions-
  erlös-Neutralisierung und die unbelegte Beratungszahl-Annahme sollten vor
  einer echten Vorstandsvorlage behoben/belegt werden.
