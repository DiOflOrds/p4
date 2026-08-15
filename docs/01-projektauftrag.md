# Projektauftrag P4 — „Mission Control 3.1: Fernzugriff & Briefkasten-Chat" (v0.1, zur G0-Freigabe)

*2026-08-15, PL. Eingang per Intake als CR auf P3 (Projektwunsch wörtlich vom Auftraggeber): (1) Mission Control im lokalen Netzwerk sichtbar machen, (2) die Team-Konversation über den Browser führen, (3) alles vom Handy (Android/Chrome) bedienbar. Zu (2) im Intake geklärt und entschieden: **Briefkasten-Chat** über den vorhandenen Session-Austausch — 0 €, asynchron, volle Team-Antworten; die Cowork-Session selbst kann nicht in den Browser umziehen, ein Live-API-Chat wurde aus Kostengründen zurückgestellt (Folge-CR möglich). G0-Freigabe: Inbox-DR T-0001.*

## Was und Warum

Mission Control ist seit P3 ein vollwertiges Arbeitswerkzeug — aber nur auf dem Team-Node unter 127.0.0.1. P4 löst es vom Schreibtisch: erreichbar von jedem Gerät im Heimnetz, bedienbar vom Handy, und mit einem Briefkasten, über den der Auftraggeber dem Team von überall Nachrichten hinterlässt, die die nächste Cowork-Session beantwortet. Weil das LAN mehr Augen hat als localhost, bekommt jeder Schreibpfad einen PIN-Schutz — sonst wäre die Entscheider-Pflicht (SWR-038) im Netzwerk wertlos.

**Zielprodukt-Typ:** Plattform/Frontend+Backend (SW, F6) · **Nutzerkreis:** Auftraggeber + Registry-Nutzer (F9), Geräte im Heim-LAN · **Vertraulichkeit:** privat, kein Internet-Expose (nur LAN; F10) · **Budget:** 0 € API (Briefkasten statt Live-Chat).

## Epics

| Epic | Inhalt | Wunsch-Bezug |
|---|---|---|
| P4-E1 | **LAN-Betrieb + PIN-Schutz:** dokumentierter Betriebsmodus mit Netzwerk-Bind (0.0.0.0) und Windows-Firewall-Freigabe; alle Schreibzugriffe (Entscheidungen, Briefkasten) verlangen eine PIN (lokal konfiguriert, nie in Git); ohne PIN bleibt alles read-only | „im Netzwerk sichtbar, von überall zugreifen" |
| P4-E2 | **Handy-Tauglichkeit:** responsive Feinschliff aller Tabs (Spalten, Tabellen, Buttons auf Touch-Größe), PWA am Android/Chrome installierbar, realer Gerätetest als Stichprobe | „über ein Handy den ganzen Mission Control aufrufen" |
| P4-E3 | **Briefkasten-Chat:** neuer Tab „Team-Chat" — Nachrichten im Browser schreiben (auch vom Handy), sie landen als versionierte Briefkasten-Dateien im Repo (Session-Austausch-Muster, sofortiger Commit wie Inbox); Antworten der nächsten Cowork-Session erscheinen im selben Verlauf; offene Nachrichten sichtbar im Cockpit | „Konversation über Mission Control führen" |

## Abnahmekriterien

1. Mission Control von einem **zweiten Gerät im LAN** erreichbar (realer Test), Betriebsmodus + Firewall-Schritte im Runbook.
2. **PIN-Schutz wirksam:** Entscheidung/Nachricht ohne bzw. mit falscher PIN wird abgelehnt (Stichprobe), mit PIN funktioniert sie; PIN liegt nur lokal (Env), nie in Git.
3. **Handy-Nachweis:** komplette Bedienung am Android/Chrome — inkl. einer echten Button-Entscheidung vom Handy (Stichprobe).
4. **Briefkasten E2E real:** Nachricht im Browser → committete Datei im Repo → Antwort aus einer Cowork-Session erscheint im Chat-Verlauf.
5. Requirements-first (SWR-Erweiterung ab SWR-048, Matrix 0 Lücken), Gates als Inbox-DRs mit Frist-Default, Aufwandsschätzung in jedem Planning.

## Rahmen

2 Sprints (S0 Anforderungen + G1 + kleines G2 — Bind/PIN/Briefkasten-Ablage als ADR-006; S1 Umsetzung + Abnahme). Playbook, Team-Node-Gate, Baselines als Tags + Manifest, Sandbox pusht nie. Sicherheits-Leitplanke: kein Port-Forwarding/Internet-Expose — nur LAN (dokumentiert im Runbook).
