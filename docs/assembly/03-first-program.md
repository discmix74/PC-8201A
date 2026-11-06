# 03 – Erstes Maschinenprogramm

## Ziel dieses Kapitels
Dieses Kapitel zeigt ein kleines, reales 8085-Programm für den PC-8201A mit sauberem Einstieg und sicherer Rückkehr zum System.

Zurück zu: [CPU-Register](02-cpu-registers.md)  
Weiter mit: [ROM2-Überblick](../rom2/01-rom2-overview.md)

## Aufbau eines Assemblerprogramms
Ein minimales Programm benötigt:

1. Startadresse (Ladeadresse im RAM)
2. Einstiegspunkt (erste auszuführende Instruktion)
3. Optional: Aufrufe von ROM-Routinen
4. Saubere Rückkehr (meist über `RET` in aufrufende Umgebung)

## Beispielprogramm (minimal)

Ziel: Einen konstanten Wert laden und sofort zurückkehren.  
Dieses Programm ist bewusst klein und dient als erster Funktionsnachweis.

```asm
		ORG 9000H      ; Programm wird ab Adresse 9000h abgelegt (Beispieladresse im freien RAM)

START:  MVI A,42H      ; Lade den Testwert 42h in Register A
		MOV B,A        ; Kopiere A nach B, damit ein zweites Register sichtbar geändert wurde
		RET            ; Rückkehr zur aufrufenden Umgebung / Monitor
```

## Schritt-für-Schritt-Erklärung

| Schritt | Was passiert? |
|---|---|
| `ORG 9000H` | Definiert, wo der Code im RAM liegen soll. |
| `MVI A,42H` | CPU schreibt 42h in den Akkumulator. |
| `MOV B,A` | Wert aus A wird nach B kopiert. |
| `RET` | CPU holt Rücksprungadresse vom Stack und kehrt zurück. |

## Speicherlage des Programms

```text
RAM (schematisch)

9000h: MVI A,42H
9002h: MOV B,A
9003h: RET
```

> Hinweis: Die genaue freie Ladeadresse muss auf dem realen Gerät geprüft werden. 9000h ist ein didaktisches Beispiel und nicht automatisch auf jeder Konfiguration frei.

## Laden und Starten auf realer Hardware
Der genaue Ablauf hängt vom eingesetzten Monitor/Assembler/Ladeweg ab. Allgemein gilt:

1. Freie RAM-Adresse festlegen (z. B. 9000h nach Prüfung).
2. Maschinenbytes oder Assemblerausgabe in diesen Bereich laden.
3. Program Counter auf den Einsprungpunkt setzen (hier: 9000h).
4. Programm starten.
5. Nach `RET` Rückkehr in das aufrufende System prüfen.

> Nicht eindeutig verifiziert in diesem Repository: konkrete Tastensequenzen bzw. Monitor-Befehle des PC-8201A in allen ROM-Versionen.

## Was der Leser dabei lernt

- wie ein Maschinenprogramm im RAM positioniert wird
- wie die CPU die Befehle nacheinander ausführt
- warum `RET` für stabile Rückkehr wichtig ist
- wie klein ein erstes funktionsfähiges Programm sein kann

## Nächster Schritt
Im nächsten Kapitel wird erläutert, wie ROM2 die Entwicklungsarbeit erweitern kann.

Weiter mit: [ROM2-Überblick](../rom2/01-rom2-overview.md)