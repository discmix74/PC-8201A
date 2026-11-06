# 01 – Was ist Assembler?

## Ziel dieses Kapitels
Dieses Kapitel erklärt den Einstieg in 8085-Assembler für den PC-8201A und führt die ersten Grundbefehle ein.

Zurück zu: [Speicherüberblick](../memory/01-memory-overview.md)  
Weiter mit: [CPU-Register](02-cpu-registers.md)

## Was ist Assembler?
Assembler ist eine menschenlesbare Schreibweise für Maschinencode. Jeder Assemblerbefehl entspricht direkt einem oder mehreren Bytes, die von der 8085-CPU ausgeführt werden.

## Warum Assembler auf dem PC-8201A?

- Direkter Zugriff auf Hardware und Speicher
- Höhere Geschwindigkeit als BASIC bei zeitkritischen Aufgaben
- Kontrolle über Register, Sprünge und ROM-Routinen
- Geeignet für kleine, effiziente Programme

## BASIC vs. Assembler

| Thema | BASIC | Assembler |
|---|---|---|
| Lesbarkeit | hoch | mittel (techniknah) |
| Ausführungsgeschwindigkeit | geringer | hoch |
| Hardwarekontrolle | begrenzt | direkt |
| Lernaufwand | niedriger Einstieg | höherer Einstieg |

## Was macht die CPU tatsächlich?
Die CPU arbeitet zyklisch:

1. Befehl aus Speicher lesen
2. Befehl dekodieren
3. Operanden verarbeiten
4. Ergebnis schreiben
5. Nächsten Befehl ausführen

Dieser Ablauf heißt vereinfacht **Fetch–Decode–Execute**.

## Erste wichtige Befehle

### MOV
- **Syntax:** `MOV ziel,quelle`
- **Beschreibung:** Kopiert ein Register oder Speicherbyte in ein Zielregister/Speicherziel.
- **Beispiel:** `MOV A,B`
- **Erklärung:** Inhalt von Register B wird nach A kopiert.

### MVI
- **Syntax:** `MVI ziel,wert`
- **Beschreibung:** Lädt einen unmittelbaren 8-Bit-Wert in ein Register oder Speicherziel.
- **Beispiel:** `MVI A,3AH`
- **Erklärung:** Register A erhält den festen Wert 3Ah.

### LXI
- **Syntax:** `LXI rp,wert16`
- **Beschreibung:** Lädt einen 16-Bit-Wert in ein Registerpaar (B, D, H) oder den Stack Pointer.
- **Beispiel:** `LXI H,8000H`
- **Erklärung:** Registerpaar HL zeigt danach auf Adresse 8000h.

### ADD
- **Syntax:** `ADD quelle`
- **Beschreibung:** Addiert Quelle zu Register A.
- **Beispiel:** `ADD C`
- **Erklärung:** A = A + C, Flags werden aktualisiert.

### SUB
- **Syntax:** `SUB quelle`
- **Beschreibung:** Subtrahiert Quelle von Register A.
- **Beispiel:** `SUB E`
- **Erklärung:** A = A - E, Flags werden aktualisiert.

### JMP
- **Syntax:** `JMP adresse`
- **Beschreibung:** Unbedingter Sprung zu einer Adresse.
- **Beispiel:** `JMP 9000H`
- **Erklärung:** Programmausführung setzt direkt an 9000h fort.

### CALL
- **Syntax:** `CALL adresse`
- **Beschreibung:** Ruft ein Unterprogramm auf; Rücksprungadresse wird auf den Stack gelegt.
- **Beispiel:** `CALL 1234H`
- **Erklärung:** CPU springt zur Routine bei 1234h.

### RET
- **Syntax:** `RET`
- **Beschreibung:** Rückkehr aus Unterprogramm; Adresse wird vom Stack geholt.
- **Beispiel:** `RET`
- **Erklärung:** Ausführung geht nach einem `CALL` an der nächsten Instruktion weiter.

## Nächster Schritt
Bevor ein vollständiges erstes Programm erstellt wird, ist ein klares Registerverständnis nötig.

Weiter mit: [CPU-Register](02-cpu-registers.md)