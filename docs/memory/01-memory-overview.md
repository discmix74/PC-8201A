# 01 – Speicherüberblick

## Ziel dieses Kapitels
Dieses Kapitel erklärt den Speicheraufbau des PC-8201A so, dass Einsteiger sicher unterscheiden können zwischen nutzbaren und geschützten Bereichen.

Zurück zu: [Systemüberblick](../getting-started/01-system-overview.md)  
Weiter mit: [Was ist Assembler?](../assembly/01-what-is-assembly.md)

## Grundprinzip
Der Adressraum eines 8085-Systems umfasst 64 KiB (0000h bis FFFFh). In diesem Raum werden ROM, RAM, Systemdaten und Programmcode organisiert.

> Wichtig: Die exakte Aufteilung kann je nach ROM-Version, RAM-Ausbau und ROM2-Konfiguration variieren. Alle konkreten Adressgrenzen müssen auf der Zielhardware verifiziert werden.

## Speicherbereiche (konzeptionell)

| Bereich | Typ | Zweck | Darf überschrieben werden? |
|---|---|---|---|
| System-ROM | ROM | Firmware, BASIC-Interpreter, feste Routinen | Nein |
| Option-ROM / ROM2 | ROM | Erweiterte Funktionen, zusätzliche Menüs/Routinen | Nein |
| Systemvariablen | RAM | Interne Zustände des Systems | Nein (nur mit genauer Kenntnis) |
| BASIC-Speicher | RAM | BASIC-Programme und BASIC-Daten | Nur im vorgesehenen Betrieb |
| Maschinenprogramm-Bereich | RAM | Eigener Assemblercode und zugehörige Daten | Ja |
| Stack-Bereich | RAM | Rücksprungadressen, temporäre CPU-Daten | Ja, aber kontrolliert |

## ASCII-Übersicht (schematisch)

```text
Adresse
FFFFh  +---------------------------------------------+
	   | Oberer RAM-Bereich / Stack (modellabhängig) |
	   +---------------------------------------------+
	   | Freier RAM für Maschinenprogramme           |
	   +---------------------------------------------+
	   | BASIC-Programm + BASIC-Variablen            |
	   +---------------------------------------------+
	   | Systemvariablen / Arbeitsbereiche           |
	   +---------------------------------------------+
	   | Option-ROM / ROM2 (falls eingeblendet)      |
	   +---------------------------------------------+
0000h  | System-ROM (Start, Routinen, BASIC-Kern)    |
	   +---------------------------------------------+
```

## Wo liegen Programme und Variablen?

| Frage | Typische Antwort |
|---|---|
| Wo wird BASIC gespeichert? | Im BASIC-RAM-Bereich |
| Wo liegt Assemblercode? | In einem freien RAM-Bereich für Maschinenprogramme |
| Wo liegen CPU-Register? | In der CPU selbst (nicht im RAM) |
| Wo liegen Systemzustände? | In reservierten Systemvariablen im RAM |
| Wo liegen ROM2-Funktionen? | Im Option-ROM/ROM2-Bereich |

## Kritische Sicherheitsregel
Bestimmte Bereiche dürfen nicht überschrieben werden:

- ROM-Bereiche (physisch nicht beschreibbar, aber falsche Sprünge können Abstürze verursachen)
- Systemvariablen ohne genaue Dokumentation
- Stack-Bereich während aktiver Unterprogramme

## Praktisches Vorgehen für eigene Programme
Vor dem Laden eines Maschinenprogramms immer prüfen:

1. Verfügbare freie RAM-Region ermitteln.
2. Kollision mit BASIC-Speicher ausschließen.
3. Kollision mit Systemvariablen ausschließen.
4. Einsprung- und Rücksprungstrategie festlegen.

## ROM2-Speichernutzung (Vorblick)
ROM2 erweitert je nach Konfiguration die nutzbaren Entwicklerfunktionen und kann zusätzliche Speicher-/Menülogik bereitstellen. Die konkrete Speicheraufteilung wird im ROM2-Kapitel separat behandelt.

Weiter mit: [Was ist Assembler?](../assembly/01-what-is-assembly.md)