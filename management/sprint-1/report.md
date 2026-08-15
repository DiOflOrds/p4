# Sprint-1-Report — P4 „Mission Control 3.1" (PL)

*2026-08-15. Sprint-Motto: „Vom Sofa aus". An: Mensch (G4 + P4-Abnahme via Inbox-DR T-0012). 5/5 Tickets done.*

## Sprint-Ziel: erreicht

| Ticket | Ergebnis | Schätzung | Ist |
|---|---|---|---|
| T-0007 | Planning | 10 min | 8 min |
| T-0008 | **PIN-Schutz + LAN-Betrieb** (SWR-048/049): localhost frei, remote nur mit `MC_PIN` (hmac-Vergleich), ohne gesetzte PIN Remote-Schreiben gesperrt; PIN-Feld im Kopfbereich (Session-Speicher); `mission-control-lan.cmd` (zeigt PC-Adresse, 0.0.0.0-Bind); Runbook Kap. 10 inkl. Firewall + Leitplanke | 40 min | 35 min |
| T-0009 | **Briefkasten** (SWR-050/051): `briefkasten.py` (Brief = versionierte Datei + sofortiger Commit, Antwort in derselben Datei), Konversations-API, Team-Chat-Tab mit Formular, Cockpit-Pille „N Brief(e) offen", Preflight-Hinweis „Briefkasten zuerst" | 45 min | 40 min |
| T-0010 | **Mobile-Feinschliff** (SWR-052): Media-Queries (Nav, Ein-Spalten-Board, Touch-Buttons ≥44px, KPI-Raster), Tabellen-Scroll, PWA installierbar | 20 min | 15 min |
| T-0011 | dieser Report + Retro + Abnahmebilanz | 20 min | 18 min |

**E5-Auswertung:** 135 min geschätzt, 116 min Ist (−14 % — dritte konsistente Messung).

## Abnahmebilanz K1–K5 (Projektauftrag)

| K | Kriterium | Bewertung | Evidenz |
|---|---|---|---|
| 1 | Erreichbar vom zweiten LAN-Gerät + Runbook | **erfüllt mit deiner Stichprobe** | mission-control-lan.cmd + Kap. 10; realer Gerätetest im Abnahme-DR |
| 2 | PIN-Schutz wirksam, PIN nie in Git | **erfüllt** | 6 Schutzregel-Tests (SWR-048); Falsch-PIN-Stichprobe im DR |
| 3 | Volle Handy-Bedienung inkl. Button-Entscheidung | **erfüllt mit deiner Stichprobe** | SWR-052-Feinschliff; die Handy-Entscheidung IST die DR-Antwort |
| 4 | Briefkasten E2E real | **erfüllt mit deiner Stichprobe** | Mechanik getestet (SWR-050); dein erster echter Brief + Team-Antwort nächste Session |
| 5 | Requirements-first, Inbox-Gates, Schätzung | **erfüllt** | `p4-req-v1.0` vor Umsetzung; D000–D002 via Inbox; Schätzspalte |

## KPIs

Tests **153 → 156** grün · Matrix 52/0 · 0,00 € API · alle bisherigen P4-Gates via Inbox.

## QM-Abschnitt (ungefiltert)

1. Drei der fünf Kriterien vollenden sich erst mit deinen realen Geräte-Stichproben — bewusstes Design: die Abnahme vom Handy aus IST der Nachweis. 2. Kein TLS im LAN (ADR-006-Grenze) — die Leitplanke „kein Internet-Expose" steht fett im Runbook; bitte ernst nehmen. 3. Erster echter Briefkasten-Roundtrip (K4) schließt sich, wenn die nächste Session deinen Brief beantwortet.

## Entscheidungsbedarf: G4 + P4-Abnahme → Inbox-DR T-0012
