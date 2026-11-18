# Flex-Pool — Silo-Governance

**Nachtrag-Registrierung 2026-11-18** (unregistriertes Repo gefunden/importiert).

## Was ist das
Rein statische HTML/CSS-Präsentation (13 Folien, KEIN JavaScript, keine
Interaktivität) — ein internes Strategiepapier für die **Diakonie
Gladenbach** (Renés Arbeitgeber, s. auch `Arbeits-Zeitnachweis`): ein
"Flex-Pool"-Personalmodell (2,25 VZÄ Springer-/Reserve-Team) zur
Entlastung der 5 ambulanten Pflegebezirke, inkl. Wirtschaftlichkeits-
Szenarien, Risikoanalyse, Organigramm, Roadmap. **Kein IRIS-Digital-/
AERIS-Produkt**, bewusst außerhalb der Produkthierarchie.

## Sensibilität (wichtig)
Enthält reale interne Daten: KDO-Lohngruppe/-stufe, konkrete Personalkosten-
Kalkulationen, Wirtschaftlichkeits-Szenarien, Organisationsstruktur eines
echten Arbeitgebers. **Bewusst NICHT öffentlich deployed** — anders als
`aeris-learn`/`apf-monitor`/Pflege-Faktencheck liegt dieses Dokument hinter
der bestehenden AERIS-Server-Basic-Auth (kein `auth_basic off`, kein
Eintrag auf Port 80). Live nur unter `https://212.132.117.130/flex-pool/`
mit den bestehenden AERIS-Zugangsdaten erreichbar.

## Analyse-Ergebnis 2026-11-18 (grimmiges Feedback, s. Chat-Antwort)
Technisch sauber (kein Overflow, responsive funktioniert, 0 Konsolenfehler),
aber zwei Tippfehler und mehrere inhaltlich fragwürdige Annahmen im
Finanzmodell gefunden — s. `handoff.md` für Details. Keine Primärquellen-
Verifikation von § 37.3 SGB XI oder KDO-Werten durchgeführt (reine
Code-/Logik-Analyse, kein `legal-compliance`-Lauf angefordert).
