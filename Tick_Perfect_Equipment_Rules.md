# Tick Perfect — Equipment Design Rules

## Table of Contents

1. [Stats Tracked](#stats-tracked)
2. [OSRS BiS Baseline](#osrs-bis-baseline)
3. [Armor Rules](#armor-rules)
4. [Weapon Rules](#weapon-rules)
5. [Naming Conventions](#naming-conventions)
6. [Stat Distribution (Armor)](#stat-distribution-armor)
7. [3D Model Mapping](#3d-model-mapping)
8. [Weight by Tier](#weight-by-tier)
9. [Quick Reference Summary](#quick-reference-summary)

---

## Stats Tracked

All equipment tracks 15 stats:

| Stat Category | Stats |
|---|---|
| **Attack** | Stab Attack, Slash Attack, Crush Attack, Magic Attack, Ranged Attack |
| **Defence** | Stab Defence, Slash Defence, Crush Defence, Magic Defence, Ranged Defence |
| **Strength** | Melee Strength, Ranged Strength, Magic Strength (Magic Damage %) |
| **Other** | Prayer/Spirit, Weight |

---

## OSRS BiS Baseline

All stats are derived from the actual OSRS Best-in-Slot gear sets (full set totals including helm, body, legs, boots, gloves, cape, amulet, ring):

| Style | Source Gear |
|---|---|
| **Melee** | Torva, Ferocious Gloves, Primordial Boots, Fire Cape, Torture, Berserker Ring (i), etc. |
| **Ranged** | Masori, Zaryte Vambraces, Pegasian Boots, Ava's Assembler, Anguish, Archers Ring (i), etc. |
| **Magic** | Ancestral/Virtus, Tormented Bracelet, Eternal Boots, Imbued God Cape, Occult, Seers Ring (i), etc. |

---

## Armor Rules

### Step 1 — Start with OSRS BiS

Take the full set stat totals for each combat style from OSRS.

### Step 2 — Defence Halving Formula (OSRS → Tier 3 Base)

Applied to convert OSRS BiS stats into our Tier 3 base values:

| Condition | Formula |
|---|---|
| Defence stat is **positive** | `stat / 2` |
| Defence stat is **negative** | `stat × 1.2` (penalties get slightly worse) |
| All other stats (attack, strength, prayer) | Unchanged |

### Step 3 — Tier Scaling

Applied to the Tier 3 base values:

| Tier | Positive Stats | Negative Stats | Notes |
|---|---|---|---|
| **Tier 3** | 100% | 100% | Endgame BiS |
| **Tier 2** | × 0.8 (80%) | × 1.2 (penalties worsen) | Mid progression |
| **Tier 1** | × 0.6 (60%) | × 1.4 (penalties worsen more) | Early progression |
| **Tier 0 (Novice)** | 25% of MAX across all 3 styles' Tier 3 stats | No negatives (tribrid) | Starter gear |

### Prayer Rules (Armor)

Prayer is **hardcoded** per tier and only appears on **Cape, Amulet, and Ring**:

| Tier | Total Prayer | Per Slot (Cape/Amulet/Ring) |
|---|---|---|
| Tier 3 | 9 | 3 each |
| Tier 2 | 6 | 2 each |
| Tier 1 | 3 | 1 each |
| Tier 0 | 0 | 0 |

### Accessory Rules (Amulet & Ring)

Amulets and Rings are **tribrid** (benefit all 3 combat styles):

1. Take the accessory stat portion from each style (Melee, Ranged, Magic)
2. **Remove all defensive stats** (offensive only)
3. **Apply 150% to offensive stats**
4. **Combine all three styles** into one item
5. Apply tier scaling as normal

### Achievement Cape Rules

Achievement Capes are tribrid capes that replace style-specific capes:

| Tier | How Stats Are Derived | Unlock |
|---|---|---|
| Tier 1 | Best stat from each of the Tier 1 style capes | Complete Rogue Mode on Easy |
| Tier 2 | Best stat from each of the Tier 2 style capes | Complete Rogue Mode on Medium |
| Tier 3 | Best stat from each of the Tier 3 style capes | Complete Rogue Mode on Hard |

---

## Weapon Rules

### Tier Scaling (Weapons)

Weapons scale differently from armor — tighter range, no T0:

| Tier | Multiplier | Rounding | Prayer |
|---|---|---|---|
| **T3** | 110% of OSRS BiS | Round **UP** (ceil) | +3 |
| **T2** | 90% of OSRS BiS | Round **NEAREST** | +2 |
| **T1** | 80% of OSRS BiS | Round **DOWN** (floor) | +1 |
| **T0** | ❌ None | — | — |

Players start with T1 weapons unlocked. There are no T0 weapons.

### Stat Scaling Rules (Weapons)

**Stats that DO scale with tier:**
- Stab/Slash/Crush/Magic/Ranged Attack
- Melee Strength
- Ranged Strength
- Magic Damage %
- Negative stats scale **inversely** (divide by multiplier instead of multiply)

**Stats that do NOT scale:**
- All Defensive Stats (handled separately — see below)
- Attack Speed
- Attack Range
- Special Attack Cost

### Defensive Stat Rules (Weapons)

| Item Type | Rule |
|---|---|
| **Weapons & Ammo** | All defenses = 0 (removed entirely) |
| **Offhands (Shields)** | Positive defenses ÷ 2; Negative defenses × 1.2 |

### Special Cases

- **Swift Blade / Quickblade**: Has 0 base stats in OSRS. Gets +1/+2/+3 to stab attack, slash attack, crush attack, and melee strength at T1/T2/T3 respectively.
- **Ammo**: Same item with 3 sub-variants (Arrows, Bolts, Darts) with different ranged strength values.

---

## Naming Conventions

### Armor Set Names

| Tier | Melee | Ranged | Magic | Tribrid |
|---|---|---|---|---|
| **T0** | Novice | Novice | Novice | Novice |
| **T1** | Sentinel | Scout | Initiate | — |
| **T2** | Vanguard | Hunter | Nova | — |
| **T3** | Ravager | Reaper | Oblivion | — |

### Armor Slot Names by Style

| Slot | Melee | Ranged | Magic | Novice |
|---|---|---|---|---|
| **Head** | Helm | Coif | Hood | Cap |
| **Chest** | Chestplate | Body | Robe Top | Vest |
| **Legs** | Platelegs | Chaps | Robe Bottom | Pants |
| **Feet** | Boots | Boots | Slippers | Boots |
| **Gloves** | Gauntlets | Vambraces | Sleeves | Gloves |
| **Cape** | Cape | Cloak | Mantle | Cloak |

Full item name format: `[Set Name] [Slot Name]`
Examples: "Ravager Chestplate", "Reaper Coif", "Oblivion Robe Top", "Novice Cap"

### Accessories (Tribrid)

| Tier | Amulet | Ring |
|---|---|---|
| **T0** | Amulet of Beginning | Ring of First Steps |
| **T1** | Amulet of Conviction | Ring of Echoes |
| **T2** | Amulet of Descent | Ring of Whispers |
| **T3** | Amulet of Madness | Ring of Despair |

### Achievement Capes (Tribrid)

| Tier | Name | Unlock |
|---|---|---|
| **T1** | Victor's Shroud | Easy completion |
| **T2** | Slayer's Shroud | Medium completion |
| **T3** | Champion's Shroud | Hard completion |

### Weapon Tier Prefixes

Weapons use the **armor set name** as a prefix:

| Tier | Melee Prefix | Ranged Prefix | Magic Prefix |
|---|---|---|---|
| **T1** | Sentinel | Scout | Initiate |
| **T2** | Vanguard | Hunter | Nova |
| **T3** | Ravager | Reaper | Oblivion |

Full weapon name format: `[Tier Prefix] [Base Weapon Name]`
Examples: "Ravager Moonblade", "Reaper Deathshot", "Oblivion Quickstave"

### All Weapon Names

**Melee Weapons:**

| OSRS Name | Base Name | T1 | T2 | T3 |
|---|---|---|---|---|
| Swift Blade | Quickblade | Sentinel Quickblade | Vanguard Quickblade | Ravager Quickblade |
| Blade of Saeldor | Moonblade | Sentinel Moonblade | Vanguard Moonblade | Ravager Moonblade |
| Osmumten's Fang | Jaggstab | Sentinel Jaggstab | Vanguard Jaggstab | Ravager Jaggstab |
| Noxious Halberd | Glaive | Sentinel Glaive | Vanguard Glaive | Ravager Glaive |
| Scythe of Vitur | Deathsweep | Sentinel Deathsweep | Vanguard Deathsweep | Ravager Deathsweep |
| Dragon Dagger | Dueling Dagger | Sentinel Dueling Dagger | Vanguard Dueling Dagger | Ravager Dueling Dagger |
| Crystal Halberd | Reachblade | Sentinel Reachblade | Vanguard Reachblade | Ravager Reachblade |
| Dragon Claws | Rippers | Sentinel Rippers | Vanguard Rippers | Ravager Rippers |
| Bandos Godsword | Guardbane | Sentinel Guardbane | Vanguard Guardbane | Ravager Guardbane |
| Saradomin Godsword | Divineblade | Sentinel Divineblade | Vanguard Divineblade | Ravager Divineblade |
| Elder Maul | Titanbreaker | Sentinel Titanbreaker | Vanguard Titanbreaker | Ravager Titanbreaker |
| Avernic Defender | Aegis | Sentinel Aegis | Vanguard Aegis | Ravager Aegis |

**Ranged Weapons:**

| OSRS Name | Base Name | T1 | T2 | T3 |
|---|---|---|---|---|
| Ammo (Arrows) | Arrows (Arrows) | Scout Arrows (Arrows) | Hunter Arrows (Arrows) | Reaper Arrows (Arrows) |
| Ammo (Bolts) | Arrows (Bolts) | Scout Arrows (Bolts) | Hunter Arrows (Bolts) | Reaper Arrows (Bolts) |
| Ammo (Darts) | Arrows (Darts) | Scout Arrows (Darts) | Hunter Arrows (Darts) | Reaper Arrows (Darts) |
| Toxic Blowpipe | Quickbow | Scout Quickbow | Hunter Quickbow | Reaper Quickbow |
| Webweaver Bow | Windbow | Scout Windbow | Hunter Windbow | Reaper Windbow |
| Bow of Faerdhinen | Moonbow | Scout Moonbow | Hunter Moonbow | Reaper Moonbow |
| Twisted Bow | Deathshot | Scout Deathshot | Hunter Deathshot | Reaper Deathshot |
| Black Chinchompa | Scatterboom | Scout Scatterboom | Hunter Scatterboom | Reaper Scatterboom |
| Tonalztics of Ralos | Crackshot | Scout Crackshot | Hunter Crackshot | Reaper Crackshot |
| Dragon Knives | Razors | Scout Razors | Hunter Razors | Reaper Razors |
| Scorching Bow | Stillshot | Scout Stillshot | Hunter Stillshot | Reaper Stillshot |
| Twisted Buckler | Aimguard | Scout Aimguard | Hunter Aimguard | Reaper Aimguard |

**Magic Weapons:**

| OSRS Name | Base Name | T1 | T2 | T3 |
|---|---|---|---|---|
| Eye of Ayak | Quickstave | Initiate Quickstave | Nova Quickstave | Oblivion Quickstave |
| Sanguinesti Staff | Moonstave | Initiate Moonstave | Nova Moonstave | Oblivion Moonstave |
| Tumeken's Shadow | Deathknell | Initiate Deathknell | Nova Deathknell | Oblivion Deathknell |
| Kodai Wand | Kaster | Initiate Kaster | Nova Kaster | Oblivion Kaster |
| Accursed Sceptre | Hexsceptre | Initiate Hexsceptre | Nova Hexsceptre | Oblivion Hexsceptre |
| Eldritch Nightmare Staff | Soulstave | Initiate Soulstave | Nova Soulstave | Oblivion Soulstave |
| Volatile Nightmare Staff | Blastrod | Initiate Blastrod | Nova Blastrod | Oblivion Blastrod |
| Fortified Elidinis Ward | Spellward | Initiate Spellward | Nova Spellward | Oblivion Spellward |

### Cross-Style Naming Themes

| Theme | Melee | Ranged | Magic |
|---|---|---|---|
| **Quick (3-tick fastest)** | Quickblade | Quickbow | Quickstave |
| **Moon (elegant mid-tier)** | Moonblade | Moonbow | Moonstave |
| **Death (powerful heavy)** | Deathsweep | Deathshot | Deathknell |

---

## Stat Distribution (Armor)

### Weighted Distribution

Total set stats are distributed across 8 item slots using these weights:

| Slot | Weight | Notes |
|---|---|---|
| **Chest** | 18% | Receives rounding excess |
| **Legs** | 15% | |
| **Helm** | 13% | |
| **Cape** | 12.5% | |
| **Amulet** | 12% | |
| **Ring** | 12% | |
| **Feet** | 10% | |
| **Gloves** | 7.5% | |
| **Total** | **100%** | |

### Rounding Rule

1. **Floor** each piece's stat value
2. Calculate total excess from rounding (total stat - sum of all floored values)
3. Add the excess (rounded) onto the **Chest** piece

### Prayer Distribution

Prayer is **not** distributed by weight. It uses the fixed values from the Prayer Rules table and only goes on Cape, Amulet, and Ring.

---

## 3D Model Mapping

### Armor Models

| Tier | Melee | Ranged | Magic |
|---|---|---|---|
| **T0** | None | None | None |
| **T1** | Sentinel (Grey) | Thief (Brown) | Tomb Seeker (Cyan) |
| **T2** | Sentinel (White) | Thief (Green) | Tomb Seeker (Purple) |
| **T3** | Nordic (White/Brown) | Reaper (Green) | Shadow Mage (Blue) |

---

## Weight by Tier

### Armor Weight

| Tier | Weight per Item |
|---|---|
| T0 (Novice) | 0.25 |
| T1 | 0.5 |
| T2 | 0.75 |
| T3 | 1.5 |

---

## Quick Reference Summary

### The Armor Pipeline

```
OSRS BiS Full Set Stats
    → Half positive defenses (÷2), worsen negative defenses (×1.2)
    → Apply tier scaling (100% / 80% / 60% / 25%)
    → Distribute to slots via weighted percentages
    → Floor each slot, excess goes to Chest
    → Round to nearest whole number
```

### The Accessory Pipeline

```
Take accessory portions from all 3 styles
    → Remove all defensive stats
    → Apply 150% to offensive stats
    → Combine into one tribrid item
    → Apply tier scaling
```

### The Weapon Pipeline

```
OSRS BiS Weapon Stats
    → Zero out all defenses (weapons/ammo) or halve positives & ×1.2 negatives (offhands)
    → Apply tier scaling (110% / 90% / 80%)
    → T3 rounds UP, T2 rounds NEAREST, T1 rounds DOWN
    → Add fixed prayer (+3 / +2 / +1)
    → Negative offensive stats scale inversely (÷ multiplier)
```

### Tier Overview

| Tier | Armor Multiplier | Weapon Multiplier | Prayer (Armor) | Prayer (Weapon) |
|---|---|---|---|---|
| **T3** | 100% | 110% | 3 per slot | +3 |
| **T2** | 80% | 90% | 2 per slot | +2 |
| **T1** | 60% | 80% | 1 per slot | +1 |
| **T0** | 25% (tribrid) | ❌ None | 0 | — |
