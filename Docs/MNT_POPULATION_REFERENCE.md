# MnT Population Rework – extrahierte technische Referenz

**Quellenstand:** [MnT PR #271 „Feature/population“](https://github.com/MEIOU-and-Taxes/MnT-EU5/pull/271), am 2026-09-07 in `develop` gemergt; [Merge-Commit 677f02c21c0401db13f3e9cfb97dcab7d693f7b8](https://github.com/MEIOU-and-Taxes/MnT-EU5/commit/677f02c21c0401db13f3e9cfb97dcab7d693f7b8). **Historischer MnT-1.3-Kontext, nicht Vanilla 1.4.**

## Designabsicht laut PR

- Einwohnerkapazität insgesamt geringer; verstärkter Einfluss des Klimas.
- Bevölkerungswachstum oberhalb des Kapazitätswerts soll nicht hart abgeschnitten werden, sondern durch einen **Soft Cap** auslaufen.
- MnT beschreibt bereits überbevölkerte Regionen als mögliche historisch plausible Gleichgewichtszustände.
- Der PR enthält **9 geänderte Dateien**, davon auch Änderungen **außerhalb** des Kapazitätssystems (z. B. Charakterinteraktion und Pop-Promotion). **Diese sind nicht Teil unseres Portierungsauftrags.**

## 1. Vegetation

[Originaldatei `in_game/common/vegetation/MnT_default.txt`](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/in_game/common/vegetation/MnT_default.txt).

| Vegetation | Kapazität vor PR | Kapazität nach PR | Modifier nach PR |
| --- | ---: | ---: | ---: |
| `desert` | 10 | 3 | (nicht zusätzlich definiert) |
| `sparse` | 25 | 11 | +0.30 |
| `grasslands` | 50 | 21 | +0.60 |
| `farmland` | 100 | 21 | +0.60 |
| `woods` | 50 | 18 | +0.50 |
| `forest` | 25 | 18 | +0.50 |
| `jungle` | 50 | 14 | +0.40 |

**Wesentlich:** Ackerland und Grasland erhalten im Kapazitätsteil dieselben Werte; andere Boni (Nahrung, Wirtschafts- und Bauwerte) sind deshalb **nicht** gleich.

**Nicht blind mitportieren:** Im PR wurden ebenfalls `local_road_building_time` in `desert`, `local_monthly_development_modifier` in `farmland`, `forest`, `jungle` geändert. Diese Felder nur auf ausdrücklichen Beschluss aufnehmen.

## 2. Topografie

[Originaldatei `in_game/common/topography/MnT_default.txt`](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/in_game/common/topography/MnT_default.txt).

| Topografie | Im MnT-Diff ergänzt | Neuer Wert |
| --- | --- | ---: |
| `mountains` | `local_population_capacity_modifier` | −0.15 |
| `hills` | `local_population_capacity_modifier` | −0.05 |
| `wetlands` | `local_population_capacity_modifier` | −0.15 |

**Achtung:** „Ergänzt“ meint: in der *Vorgängerversion von MnT* stand dort kein entsprechender Eintrag. Das ist kein verlässlicher Vanilla-1.4-Vorher-Wert. Außerdem hat der [1.4-Kompatibilitätsbranch (gepinnt)](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/2d6c59b9f32ac3f52e35ccd073099211738d4e15/in_game/common/topography/MnT_default.txt) bereits teils strukturell andere 1.4-Syntax, u. a. bei `proximity`.

## 3. Klima

[Originaldatei `in_game/common/climates/MnT_default.txt`](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/in_game/common/climates/MnT_default.txt).

In PR #271 werden neue absolute `local_population_capacity`-Werte eingeführt und viele Klimamultiplikatoren angepasst. Die folgende Tabelle enthält die 30 **im referenzierten Merge-Commit ausdrücklich mit Grundwert** definierten Klimazonen.

| Klima-ID | Kapazität | `local_population_capacity_modifier` |
| --- | ---: | ---: |
| `rainforest_climate` | 7 | 0.35 |
| `monsoon_climate` | 11 | 0.4 |
| `savanna_winter_climate` | 7 | 0.3 |
| `savanna_summer_climate` | 7 | 0.25 |
| `hot_desert_climate` | 2 | -0.25 |
| `cold_desert_climate` | 2 | -0.35 |
| `hot_steppe_climate` | 2 | -0.25 |
| `cold_steppe_climate` | 2 | -0.30 |
| `mediterranean_climate` | 14 | 0.65 |
| `oceanic_mediterranean_climate` | 14 | 0.65 |
| `subalpine_mediterranean_climate` | 7 | 0.35 |
| `monsoon_humid_subtropical_climate` | 14 | 0.60 |
| `monsoon_oceanic_climate` | 11 | 0.45 |
| `monsoon_subpolar_oceanic_climate` | 4 | 0.2 |
| `humid_subtropical_climate` | 14 | 0.6 |
| `oceanic_climate` | 11 | 0.50 |
| `subpolar_oceanic_climate` | 3 | 0.1 |
| `mediterranean_continental_climate` | 7 | 0.30 |
| `mediterranean_hemiboreal_climate` | 2 | -0.15 |
| `mediterranean_boreal_climate` | 2 | -0.15 |
| `mediterranean_hypercontinental_climate` | 2 | -0.3 |
| `monsoon_continental_climate` | 7 | 0.35 |
| `monsoon_hemiboreal_climate` | 4 | 0.25 |
| `monsoon_boreal_climate` | 2 | -0.20 |
| `monsoon_hypercontinental_climate` | 2 | -0.35 |
| `continental_climate` | 7 | 0.35 |
| `hemiboreal_climate` | 7 | 0.30 |
| `boreal_climate` | 1 | -0.25 |
| `hypercontinental_climate` | 1 | -0.35 |
| `andean_tundra_climate` | 2 | -0.2 |

Zusätzlich existieren dort `tundra_climate` und `polar_climate` mit Kapazitätsmodifiern, aber ohne neuen absoluten Kapazitätseintrag (im extrahierten Merge-Stand). Es handelt sich um **MnT-eigene bzw. umbenannte Klimakategorien**; die 1.4-Vanilla-Klima-IDs und die betroffenen Karten-/Location-Zuordnungen **zwingend abgleichen**, bevor sie portiert werden.

## 4. Siedlungsränge

[Originaldatei `in_game/common/location_ranks/MnT_default.txt`](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/in_game/common/location_ranks/MnT_default.txt).

| MnT-Rang | Grundkapazität vor → nach PR | Modifier vor → nach PR |
| --- | --- | --- |
| `town` | 10 → 5 | 0.10 → 0.20 |
| `city` | 70 → 10 | 0.25 → 0.40 |
| `megalopolis` | 350 → 40 | 0.50 → 0.70 |

Der PR entfernt zusätzlich den negativen `local_monthly_food_modifier` bei `megalopolis`. Das ist eine **weitere** Balanceentscheidung, kein zwingender Bestandteil unserer Kapazitäts-Mod.

**Nicht übernehmen:** Weitere MnT-spezifische Voraussetzungen für Rangaufstiege (z. B. eigene `urban_amenities`-Gebäude) sowie militärische/ökonomische Ranking-Modifikatoren, sofern eine reine Kapazitätsmod entstehen soll.

## 5. Flüsse und Küsten

[Originaldatei `main_menu/common/static_modifiers/MnT_location.txt`](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/main_menu/common/static_modifiers/MnT_location.txt).

| Modifier | Kapazität nach PR | Kapazitätsmodifier nach PR |
| --- | ---: | ---: |
| `river_flowing_through_1` | +2 | +0.05 |
| `river_flowing_through_2` | +4 | +0.10 |
| `river_flowing_through_3` | +6 | +0.15 |
| `river_flowing_through_4` | +8 | +0.20 |
| `river_flowing_through_5` | +10 | +0.25 |
| `coastal` | +4 | +0.10 |

**Hinweis:** Der ursprüngliche MnT-Stand hatte für die fünf Flussstufen Modifier 0.10 / 0.20 / 0.30 / 0.40 / 0.30 und für `coastal` 0.25. `river_flowing_through_coast_X` ist dagegen im PR für Hafen-Eignung definiert und kein zusätzlicher Kapazitätsbonus.

## 6. Überbevölkerung: Soft Cap

[Originaldatei `main_menu/common/static_modifiers/MnT_location.txt`](https://github.com/MEIOU-and-Taxes/MnT-EU5/blob/677f02c21c0401db13f3e9cfb97dcab7d693f7b8/main_menu/common/static_modifiers/MnT_location.txt).

Im neu eingeführten `REPLACE:overpopulation`:
- Die alte `cap_maximum_population_growth_at_zero = yes`-Wirkung ist **auskommentiert**.
- `local_population_growth = -0.005` als neuer Malus hinzugefügt.
- `local_pop_demotion_speed_modifier = 0.5` sowie `local_migration_attraction = -25.0` vorhanden.
- `local_migration_speed = 0.15` (im PR-Kommentar „from 0.05“).
- `local_mercenaries_modifier = 0.5` vorhanden.

Da der Modifier laut Quellkommentar mit Überbevölkerung skaliert, ist die **effektive Wachstumsfunktion** nicht allein aus dieser Definition mathematisch belegbar. Konkretes Verhalten muss per Engine und Location-Tooltip getestet werden.

## 7. Klassifikation für Portierung

**Kern:**
- Vegetationskapazität und Topografiemodifier (Pflicht bei Terrain-only-Prototyp).
- Klima, Ränge, Fluss/Küste und Soft Cap sind fachlich **Teil des gesamten MnT-Populationsreworks**, aber ein **eigener Ausbauumfang**.

**Explizit nicht Ziel:**
- MnT-Charakterverbannung und `pop_types`-Promotion-Rework.
- Andere Änderungen an Baukosten, Straßenbau, Entwicklung, RGO und Militär.
- MnT-Mod-Dependency; die eigenständige Mod soll nur benötigte Vanilla-Definitionen gezielt ersetzen.

## 8. Bekannte Portierungsrisiken

1. **1.3 → 1.4:** 1.4-Syntax, Klima-IDs und Vanilla-Dateien lokal gegentesten.
2. **`REPLACE:` überschreibt ganze Objekte:** nicht nur die 2 Kapazitätszeilen übernehmen; übrige 1.4-Vanilla-Felder unverändert erhalten.
3. **Dateipfade getrennt:** `in_game/common/{vegetation,topography,climates,location_ranks}/`; `main_menu/common/static_modifiers/`.
4. **Spielversion:** die PR-Quelle war bei Merge als `supported_game_version = 1.3.*` deklariert; der spätere Kompatibilitätsbranch ist ein *separates* 1.4-Beispiel.
5. **Prüfstatus:** Zahlen und Diff sind geprüft; Gameplay-Auswirkungen oder Ingame-Ladefähigkeit sind **noch nicht verifiziert**.
