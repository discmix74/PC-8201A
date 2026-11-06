# 02 – CPU-Register (Intel 8085)

## Ziel dieses Kapitels
Dieses Kapitel erklärt die Register und Flags der 8085-CPU als Vorbereitung für das erste lauffähige Programm.

Zurück zu: [Was ist Assembler?](01-what-is-assembly.md)  
Weiter mit: [Erstes Programm](03-first-program.md)

## Registerübersicht

| Register | Größe | Funktion |
|---|---:|---|
| A | 8 Bit | Akkumulator für Rechen- und Logikoperationen |
| B | 8 Bit | Allgemeines Register |
| C | 8 Bit | Allgemeines Register |
| D | 8 Bit | Allgemeines Register |
| E | 8 Bit | Allgemeines Register |
| H | 8 Bit | Oberes Byte des Adresspaares HL |
| L | 8 Bit | Unteres Byte des Adresspaares HL |
| PC (Program Counter) | 16 Bit | Adresse des nächsten Befehls |
| SP (Stack Pointer) | 16 Bit | Zeiger auf aktuellen Stackbereich |

## Registerpaare
Die 8085 kann Register als Paare nutzen:

- BC
- DE
- HL

HL wird häufig als Speicherzeiger eingesetzt.

## Flags (Statusbits)

| Flag | Bedeutung |
|---|---|
| Z (Zero) | Ergebnis ist 0 |
| S (Sign) | Höchstes Bit des Ergebnisses ist 1 |
| P (Parity) | Ergebnis hat gerade Parität |
| CY (Carry) | Übertrag/Entleihung bei Rechenoperationen |
| AC (Aux Carry) | Hilfsübertrag für BCD-bezogene Operationen |

Flags werden durch viele Befehle automatisch gesetzt oder gelöscht und steuern bedingte Sprünge.

## Beispiel: Registerfluss nachvollziehen

```asm
MVI A,05H    ; A = 05h
MVI B,03H    ; B = 03h
ADD B        ; A = 08h, Flags werden gesetzt
SUB B        ; A = 05h, Flags werden neu gesetzt
```

## Warum PC und SP entscheidend sind

- **PC** bestimmt, welcher Befehl als Nächstes ausgeführt wird.
- **SP** ist kritisch für `CALL`/`RET`, da Rücksprungadressen über den Stack verwaltet werden.
- Falsche SP-Nutzung führt schnell zu Abstürzen oder Rücksprung in falsche Adressen.

## Verbindung zum nächsten Kapitel
Im nächsten Kapitel wird ein minimales Maschinenprogramm Schritt für Schritt aufgebaut, geladen und gestartet.

Weiter mit: [Erstes Programm](03-first-program.md)