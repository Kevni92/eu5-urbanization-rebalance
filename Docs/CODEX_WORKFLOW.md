# Codex-Handoff: EU5 Urbanization Rebalance (1.4 Beta)

**Repository ist die Project Source of Truth** für Designentscheidungen, Quellenstatus und Mod-Artefakte. Die **EU5-Engine der tatsächlich installierten Version** bleibt die letzte Instanz für Syntax und Laufzeitverhalten.

## Auftrag

Entwickle eine **eigenständige EU5-Mod** auf Basis der gezielten Bevölkerungskapazitäts-Änderungen aus MnT PR #271. **Keine Abhängigkeit von MEIOU & Taxes** einführen. Dokumentationsarbeit und Implementierungsarbeit getrennt halten.

### Ausbaustufen (keine ungeprüfte Komplettübernahme)

1. **Terrain-only (Minimum):** sieben Vegetationswerte + drei topografische Kapazitätsmodifier aus `MNT_POPULATION_REFERENCE.md` portieren.
2. **Population-capacity-komplett (optional):** klimabasierte absolute Werte/Modifier, Ränge, Fluss- und Küsteneffekte übernehmen, aber mit **1.4 Vanilla-Klimaklassifikation** abgleichen und die Quelle jeder Portierungsentscheidung dokumentieren.
3. **Wachstumsmodell (optional, eigener Testfall):** `overpopulation`-Soft-Cap getrennt entwickeln und gegen Vanilla 1.4 testen.
4. **Nicht portieren:** nicht-populationsrelevante MnT-Anpassungen an Gesellschaftsschichten, Gebäude, Wirtschaft, Bauzeiten oder Kampfmechaniken.

Wenn der Zielumfang im Repository nicht entschieden ist, **Terrain-only als konservativen Ausgangspunkt** ansehen und keine versteckten zusätzlichen Gameplay-Änderungen implementieren.

## Workflow je Änderung

1. **Iststand lesen:** `AGENTS.md`, `Docs/README.md`, `Docs/SOURCES.md`, `Docs/EU5_1_4_BETA.md`, `Docs/MNT_POPULATION_REFERENCE.md`.
2. **Versionsprüfung:** tatsächlichen 1.4-Beta-Build der lokalen EU5-Installation bestimmen und die lokalen Vanilla-Dateien derselben Version lesen.
3. **Syntaxbeweis:** betroffene Modifier und Definitionstypen in den gepinnten Engine-Dumps prüfen; ggf. neuere Dumps der installierten Version generieren.
4. **Selektiver Port:** die **vollständige 1.4-Vanilla-Objektdefinition** als Basis nehmen; gezielt nur verifizierte Kapazitätsfelder ändern, nötigenfalls `REPLACE:<id>` nutzen. Bei abweichendem Originalformat nicht blind MnT-1.3-Dateien kopieren.
5. **Datei- und Override-Audit:** gleicher Pfad/Typerkennung wie im lokalen Vanilla-Verzeichnis; keine doppelten IDs, keine unbeabsichtigten Änderungen anderer Gameplay-Felder.
6. **Test:** statisches Format/Encoding, Fehlerlog, Laden im Spiel und Vergleich konkreter Location-Kapazitäten bei Vegetation/Topografie/Klima/Siedlungsrang/Küste/Fluss.
7. **Dokumentation:** jede neue verifizierte Quelle oder Abweichung in `Docs/SOURCES.md` und `Docs/MNT_POPULATION_REFERENCE.md` aufnehmen; Testergebnisse deutlich als *bestanden*, *fehlgeschlagen* oder *nicht durchgeführt* kennzeichnen.

## Verbindliche Prüfschritte

- Bestehende Definitionen von `REPLACE`-Objekten gegenüber 1.4-Vanilla **Feld für Feld** differenzieren. Jede Nebenänderung auflisten.
- Eine **positive Kontrollprobe** muss zeigen, dass Änderungen wirklich geladen wurden (nicht nur „keine Fehler im Log“).
- Beispielhafte Kontroll-Standorte wählen: `grasslands` gegenüber `farmland`, `desert` gegenüber `jungle`, `flatland` gegenüber `mountains`, mit sonst möglichst gleichen Faktoren. Bei Abweichungen andere Einflüsse im Tooltip berücksichtigen.
- Falls später Klima-/Rangänderungen aufgenommen werden: vorher/nachher-Berechnung anhand tatsächlicher Locations und additive versus multiplikative Anwendung belegen, nicht raten.
- `overpopulation`-Effekte separat testen: unter Kapazität, nahe Kapazität, über Kapazität, Migration/Netto-Wachstum.
- `metadata.json` auf `1.4.*` auslegen **nur wenn** diese Version tatsächlich getestet/gezielt unterstützt wird; keine Funktionsgarantie daraus ableiten.

## Repo- und Release-Hygiene

- `Docs/`: Research, Provenienz und Tests, **nicht** direkt als ausgelieferter Mod-Content.
- `.metadata/`, `in_game/`, `main_menu/`: nur nach 1.4-Verifikation als eigentliche EU5-Mod-Daten einsetzen.
- `AGENTS.md`: dauerhaftes Agentenbriefing.
- `README.md`: Projektstatus und wichtigste Hinweise.
- Keine fremden vollständigen Gamefile-Mirror oder Mega-Dumps ungeprüft in Git kopieren. Quellenstände über permanente Commits referenzieren.
- Änderungen, die einen anderen Mod überschreiben können, als **Konfliktpotential** markieren.

## Codex-Aufgabe beim ersten lokalen Start

1. Bestätige die 1.4-Beta-Spielversion und die für Mods geltende Dateistruktur.
2. Erstelle einen *read-only* Vergleich der relevanten 1.4-Vanilla-Definitionen mit `Docs/MNT_POPULATION_REFERENCE.md`.
3. Protokolliere Unterschiede und nötige 1.4-Syntaxänderungen, bevor Dateien überschrieben werden.
4. Implementiere anschließend den kleinsten testbaren Terrain-only-Prototyp, sofern keine weitergehende Projektspezifikation vorliegt.
5. Kennzeichne alle noch nicht im Spiel getesteten Arbeiten ausdrücklich als ungetestet.
