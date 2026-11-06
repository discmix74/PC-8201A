# 01 – Systemüberblick: NEC PC-8201A

## Ziel dieses Kapitels
Dieses Kapitel erklärt, was der NEC PC-8201A ist, welche Hardware-Grundlagen relevant sind und warum ROM/RAM für die Entwicklung zentral sind.

Weiter mit: [Speicherüberblick](../memory/01-memory-overview.md)

## Was ist der NEC PC-8201A?
Der NEC PC-8201A ist ein tragbarer 8-Bit-Computer aus den 1980er Jahren. Er gehört zur Gerätefamilie, die auch als Plattform für den TRS-80 Model 100 bekannt ist. Das System wurde für mobile Texteingabe, Kommunikation und BASIC-Programmierung entwickelt.

## Hardware-Grundlagen

| Bereich | Kurzbeschreibung |
|---|---|
| CPU | Intel 8085 (8-Bit), steuert alle Programmabläufe |
| ROM | Fester Programmspeicher mit Systemfunktionen (z. B. BASIC, Menü, Routinen) |
| RAM | Schreibbarer Arbeitsspeicher für Programme und Daten |
| Anzeige/Tastatur | Interaktive Bedienung direkt am Gerät |
| Option-ROM | Erweiterbarer Bereich für zusätzliche Firmware-Funktionen |

## Welche CPU ist verbaut?
Im PC-8201A arbeitet eine **Intel 8085 CPU**. Für Entwickler ist wichtig:

- Die CPU verarbeitet Maschinenbefehle sequentiell.
- Register und Flags steuern Rechenoperationen und Sprungverhalten.
- Assemblercode wird direkt als 8085-Maschinencode ausgeführt.

## Unterschiede zum TRS-80 Model 100
Der PC-8201A und der TRS-80 Model 100 sind technisch eng verwandt. In der Praxis gilt:

- Die Grundarchitektur ist sehr ähnlich.
- ROM-Inhalte, Menüdetails und einzelne Routinen können je nach Modell/ROM-Version abweichen.
- Quelltexte und Routinenadressen müssen daher immer gegen die konkrete Zielhardware geprüft werden.

> Hinweis: Exakte Differenzlisten sind versionsabhängig und werden in späteren Kapiteln ergänzt, sobald sie quellenbasiert verifiziert sind.

## Rolle von ROM und RAM

| Speicherart | Bedeutung in der Entwicklung |
|---|---|
| ROM | Enthält dauerhaft vorhandene Systemroutinen. Entwickler können diese Routinen aufrufen, statt Funktionen neu zu schreiben. |
| RAM | Enthält zur Laufzeit eigene Programme, Variablen, Stapel (Stack) und temporäre Daten. |

## Systembild (vereinfacht)

```text
+---------------------------------------------------------+
| NEC PC-8201A                                            |
|                                                         |
|  +-------------------+      +------------------------+  |
|  | Intel 8085 CPU    | <--> | ROM (System/Firmware) |  |
|  +-------------------+      +------------------------+  |
|           |                          ^                  |
|           v                          |                  |
|  +-------------------+      +------------------------+  |
|  | RAM (Programme,   | <--> | I/O (Tastatur/Anzeige)|  |
|  | Variablen, Stack) |      +------------------------+  |
|  +-------------------+                                 |
+---------------------------------------------------------+
```

## Warum dieses Wissen wichtig ist
Für jede Assembleranwendung müssen vier Fragen geklärt sein:

1. Wo liegt der Code im RAM?
2. Welche ROM-Routinen werden verwendet?
3. Welche Speicherbereiche dürfen verändert werden?
4. Wie erfolgt die sichere Rückkehr zum System?

Diese Punkte werden im nächsten Kapitel systematisch auf den Speicheraufbau angewendet.

Weiter mit: [Speicherüberblick](../memory/01-memory-overview.md)