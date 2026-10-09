# Docs – Source of Truth für EU5 Urbanization Rebalance

**Arbeitsstand:** 2026-10-09 · **Zielversion:** Europa Universalis V 1.4 Beta (`1.4.0-beta`) · **Status:** Recherche und Portierung, **kein Ingame-Test bestätigt**.

Dieses Verzeichnis ist die **kanonische, versionierte Projektdokumentation** für den lokalen Codex-Agenten. Der aktuell geprüfte Sachstand steht hier im Repository; externe Repositories sind **nachweisbare Upstream-Quellen**, aber dürfen nicht ohne Versionsprüfung als unmittelbar gültige Spielregel behandelt werden.

## Einstieg

1. [SOURCES.md](SOURCES.md) – priorisierte Quellen, feste Commits, Links, Gültigkeitsbereiche und Lücken.
2. [EU5_1_4_BETA.md](EU5_1_4_BETA.md) – indexierte 1.4-Beta-Engine-Dumps, Readmes, Versionierung.
3. [MNT_POPULATION_REFERENCE.md](MNT_POPULATION_REFERENCE.md) – konkrete aus MnT PR #271 verifizierte Werte für Vegetation, Topografie, Klima, Siedlungsränge, Flüsse und Überbevölkerung.
4. [CODEX_WORKFLOW.md](CODEX_WORKFLOW.md) – Auftrag, Implementierungsgrenzen, Verifikation und Tests.

Zusätzlich gilt im Repository-Root [AGENTS.md](../AGENTS.md) als kurze Codex-Einstiegsanweisung.

## Quellen- und Wahrheitsmodell

- **Projektentscheidungen / Zielumfang:** Diese Docs und der später im selben Repo versionierte Mod-Code.
- **Gültigkeit von EU5-Syntax:** Engine-Dumps der **exakt installierten** Spielversion; danach Vanilla-Dateien **derselben Version**.
- **Mechanikvorbild:** MnT PR #271, als 1.3-basiertes Designbeispiel. Die 1.4-Kompatibilitätsarbeit ist separat referenziert.
- **Bei Unklarheit:** Nicht stillschweigend auf 1.3-Dateien zurückfallen. Fundstelle, Version und offene Prüfung dokumentieren.

**Wichtig:** Die vollständigen Vanilla-Gamefiles der 1.4 Beta sind *nicht* Bestandteil dieses Repositorys und werden in diesen Docs *nicht* vorgetäuscht. Ebenso werden die großen Community-Engine-Dumps hier nicht ungeprüft gespiegelt. Stattdessen sind die Originaldateien in `SOURCES.md` / `EU5_1_4_BETA.md` per unveränderlichem Commit verlinkt.

## Für Codex

Vor jeder Änderung `AGENTS.md` und diese vier Dateien lesen; bei Engine-Syntax die verlinkten 1.4-Dumps und die lokale EU5-Installation überprüfen. Änderungen dokumentieren, Tests mit positiven Kontrollfällen durchführen und Ergebnisse nach `Docs/` zurückschreiben.
