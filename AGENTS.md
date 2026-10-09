# Anweisungen für Codex / AI-Agenten

Dieses Repository ist die **verbindliche Projektquelle** für `eu5-urbanization-rebalance`.

**Zuerst lesen (in dieser Reihenfolge):**
1. [Docs/README.md](Docs/README.md)
2. [Docs/SOURCES.md](Docs/SOURCES.md)
3. [Docs/EU5_1_4_BETA.md](Docs/EU5_1_4_BETA.md)
4. [Docs/MNT_POPULATION_REFERENCE.md](Docs/MNT_POPULATION_REFERENCE.md)
5. [Docs/CODEX_WORKFLOW.md](Docs/CODEX_WORKFLOW.md)

**Ziel:** eigenständige EU5-1.4-Beta-Mod für überarbeitete Location-Bevölkerungskapazitäten. Designbasis ist MnT PR #271; **keine MnT-Abhängigkeit**.

**Zwingende Regeln:**
- Bei Konflikten technischer Syntax gelten lokale **Vanilla-1.4-Dateien und Engine-Dumps derselben installierten Buildnummer** vor diesen Notizen.
- `Docs/` enthält verifizierte MnT-Daten und gepinnte Links, **keine verifizierten vollständigen Vanilla-1.4-Gamefiles**.
- Nie MnT-1.3-Definitionen komplett in 1.4 kopieren; nach lokalen Vanilla-Definitionen portieren.
- Nur verlangte Population-Capacity-Felder modifizieren. Keine versteckten Nebenänderungen.
- Keine unbekannten Trigger/Effects/Dateipfade erfinden. Nicht verifizierte Punkte offen markieren.
- Testen: statisch, Error-Logs, positive Ingame-Kapazitätskontrollprobe.
- Jede neue Quelle, Versionsabweichung und Testentscheidung in `Docs/` aktualisieren.
- Beim ersten lokalen Start die [Codex-Handoff-Aufgaben](Docs/CODEX_WORKFLOW.md) abarbeiten.

**Sprache der Dokumentation:** Deutsch; EU5-Schlüssel/Identifier im exakten Original.
