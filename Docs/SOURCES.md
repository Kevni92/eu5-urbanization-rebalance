# Quellenregister – EU5 Urbanization Rebalance

**Zuletzt verifiziert:** 2026-10-09. Die hier angegebenen SHA-Links sind reproduzierbare Snapshots; bewegliche Branches sind ausdrücklich als solche bezeichnet.

## Verifikationshierarchie

1. **Gleicher Spielbuild, höchste technische Autorität:** lokale EU5-1.4-Beta-Installation einschließlich generierter `script_docs`, `dump_data_types` und Vanilla-Definitionen.
2. **1.4-Beta-Engine-Dump als öffentlicher Ersatz:** Modding-Co-op `modding-digests`, Commit `00be0118d79294196dcb8197ded22b3656109910`.
3. **MnT-Implementierung als fachliche Vorlage:** gemergter PR #271 / Merge-Commit `677f02c21c0401db13f3e9cfb97dcab7d693f7b8`. Das ist ein **1.3-Kontext**, nicht Vanilla 1.4.
4. **MnT-Port nach 1.4 als zusätzliches Beispiel:** Branch `feature/Rio_Salado_Compatibility`, inspizierter Commit `2d6c59b9f32ac3f52e35ccd073099211738d4e15`. Der Name des Branches allein garantiert keine vollständige 1.4-Kompatibilität.
5. **Ältere Vanilla-Spiegelung nur als historische Referenz:** `HLJSXK/eu5-towards-victory`, zuletzt dokumentierter EU5-1.3-Sync `5f58b0370d07d57b6041c8bc60a59793b8967225`. **Nicht** als 1.4-Syntaxbeweis verwenden.

## Primärquellen (GitHub, fest auf Commits)

| Kennung | Quelle | Nutzung | Einschränkung |
| --- | --- | --- | --- |
| ENGINE14 | [Modding Digests 1.4.0-beta](https://github.com/Europa-Universalis-5-Modding-Co-op/modding-digests/tree/00be0118d79294196dcb8197ded22b3656109910/1.4/1.4.0) | 1.4 Script-Diffs, Typdefinitionen und Originaldumps | Community-Export; gegen lokalen Build prüfen |
| ENGINE14-CURRENT | [Aktuelle Dokumentationslogs (gepinnt)](https://github.com/Europa-Universalis-5-Modding-Co-op/modding-digests/tree/00be0118d79294196dcb8197ded22b3656109910/current_docs) | Effects, Triggers, Modifier, Scopes und Datentypen | Stand 1.4.0-beta, keine Vanilla-Gamefile-Kopie |
| MNT-PR271 | [Population-Rework-PR #271](https://github.com/MEIOU-and-Taxes/MnT-EU5/pull/271) | fachliches Ziel und Reviewhistorie | 2026-09-07 gemergt, ursprünglich 1.3 |
| MNT-PR271-SHA | [Merge-Commit 677f02c](https://github.com/MEIOU-and-Taxes/MnT-EU5/commit/677f02c21c0401db13f3e9cfb97dcab7d693f7b8) | auditierbarer Diff für Vegetation, Klima, Topografie, Ränge, Küste, Flüsse, Soft Cap | enthält weitere MnT-Änderungen, **nicht alles portieren** |
| MNT-RIO14 | [MnT-Branch-Kompatibilitätsstand (gepinnt)](https://github.com/MEIOU-and-Taxes/MnT-EU5/tree/2d6c59b9f32ac3f52e35ccd073099211738d4e15) | Beispiel neuer 1.4-Syntax, insbesondere Topografie/Proximity | laufende Feature-Branch, Funktionstest ausstehend |
| VANILLA13 | [Älterer Vanilla-Gamefile-Mirror](https://github.com/HLJSXK/eu5-towards-victory/tree/5f58b0370d07d57b6041c8bc60a59793b8967225/reference_game_files/game) | Orientierung für Pfade und historische Vergleiche | **Version 1.3, nicht 1.4** |

## Relevante Originaldateien in MnT PR #271

- [Vegetation](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/in_game/common/vegetation/MnT_default.txt)
- [Topografie](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/in_game/common/topography/MnT_default.txt)
- [Klima](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/in_game/common/climates/MnT_default.txt)
- [Siedlungsränge](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/in_game/common/location_ranks/MnT_default.txt)
- [Statische Standortmodifier (Flüsse, Küsten, Überbevölkerung)](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/main_menu/common/static_modifiers/MnT_location.txt)
- [Gebäude (Urban Amenities)](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/in_game/common/building_types/town_buildings.txt)

## Weitere Kontextquelle

- [MnT-Balancing-Tabelle](https://docs.google.com/spreadsheets/d/1ZY1k7X1LymSPdtjcGXBNXomkm0Gz-th-1-Q6PoS4nbY/edit) – in MnT-Quellkommentaren genannt, **in dieser Recherche nicht tabellarisch verifiziert**; daher keine daraus abgeleiteten Zahlen.
- [1.4-Beta-Änderungsdigest](https://github.com/Europa-Universalis-5-Modding-Co-op/modding-digests/blob/00be0118d79294196dcb8197ded22b3656109910/1.4/1.4.0/changes_files.md) – Änderungsindex, **kein vollständiger 1.4-Vanilla-Dateimirror**.

## Offene Quellenlücken

- Keine vollständigen, hier verifizierten **Vanilla 1.4 Beta Gamefiles** in diesem Repository.
- Kein bestätigter Test gegen die lokal installierte Spiel-Buildnummer; `1.4.0-beta` ist **nicht** automatisch jeder spätere 1.4-Beta-Hotfix.
- Die technische Zusammensetzung der maximalen Location-Bevölkerung einschließlich Reihenfolge / Multiplikation aller Faktoren ist ohne Live-Tooltip/Engine-Validierung nicht abschließend bewiesen.

**Regel:** In `Docs/MNT_POPULATION_REFERENCE.md` sind Werte *extrahierte MnT-Werte*; sie sind weder eine Vanilla-1.4-Spezifikation noch ein bestätigter Port. Bei neuer Verifikation zuerst neue Quelle + Commit erfassen, dann diese Docs konsistent aktualisieren.
