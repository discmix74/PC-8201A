# 01 – ROM2-Überblick

## Ziel dieses Kapitels
Dieses Kapitel führt in ROM2 von CloeSou ein und beschreibt, wie ROM2 als Entwicklungsbasis für eigene Programme genutzt werden kann.

Zurück zu: [Erstes Programm](../assembly/03-first-program.md)

## Was ist ROM2?
ROM2 ist eine alternative bzw. ergänzende ROM-Erweiterung für die PC-8201A-/Model-100-Familie. Ziel ist es, zusätzliche Funktionen für Anwender und Entwickler bereitzustellen.

## Welche Probleme löst ROM2?

- Erweiterung gegenüber Standard-ROM-Funktionen
- Potenziell bessere Struktur für zusätzliche Programme
- Potenzielle Erleichterung bei Menüintegration eigener Anwendungen

> Wichtig: Der konkrete Funktionsumfang hängt von der verwendeten ROM2-Version ab und muss gegen die zugehörige Dokumentation verifiziert werden.

## Unterschiede zum Standard-ROM

| Thema | Standard-ROM | ROM2 |
|---|---|---|
| Funktionsumfang | Basisfunktionen des Geräts | Erweiterungen je nach ROM2-Version |
| Entwicklerhilfen | modellabhängig begrenzt | zusätzliche Hilfen möglich |
| Menüerweiterung | standardisiert | erweiterbar (versionsabhängig) |

## Installation und Voraussetzungen

### Hardware
- Kompatibles Zielgerät (NEC PC-8201A bzw. verwandte Plattform)
- Geeignete ROM-Hardware bzw. Austausch-/Erweiterungslösung

### Konfiguration
- Korrekte ROM2-Version für die Zielhardware wählen
- Speicherlayout und Startverhalten vorab prüfen
- Vor Änderungen vollständige Sicherung des Ausgangszustands erstellen

> Nicht eindeutig verifiziert in diesem Repository: exakte Installationsschritte, Schalterstellungen und Hardware-Adapter je ROM2-Variante.

## Entwicklung mit ROM2

### Besonders wichtige Themen

- Speicheraufteilung unter ROM2
- Verfügbare Erweiterungen
- Neue Entwicklerfunktionen
- Menüintegration

Diese Punkte werden in den folgenden ROM2-Kapiteln vertieft und mit verifizierten Adressen/Beispielen ergänzt.

## Eigenes Programm in ROM2 (Ablaufmodell)
Der typische Ablauf sieht so aus:

1. Programm in vorgesehenem Speicherbereich ablegen.
2. Startadresse (Einsprungpunkt) definieren.
3. Programm im ROM2-Mechanismus registrieren.
4. Menüeintrag erzeugen.
5. Programm über Menü starten.
6. Saubere Rückkehr ins Hauptmenü sicherstellen.

> Offen / zu verifizieren: konkrete Tabellenstrukturen, Routinenadressen und Registrierungsformate für die jeweilige ROM2-Version.

## Verbindung zu den Grundlagen
ROM2 baut direkt auf den Grundlagen aus den vorherigen Kapiteln auf:

- Systemverständnis: [Systemüberblick](../getting-started/01-system-overview.md)
- Speicherlogik: [Speicherüberblick](../memory/01-memory-overview.md)
- Assemblerbasis: [Was ist Assembler?](../assembly/01-what-is-assembly.md)
- Erstes Programm: [Erstes Programm](../assembly/03-first-program.md)