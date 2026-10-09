# Into the Necrovale: drie buildsets

Stand: 9 oktober 2026. Game build 20114049.

## Eerst dit

De vorige sessie stopte voordat er builds gekozen waren. Het model liep tegen zijn gebruikslimiet aan op het moment dat de ontwerpronde startte, en de werkbestanden (simulator, zoekresultaten, spelgegevens) stonden alleen in die oude container. Ze zijn weg.

Dit document is opgebouwd uit wat in het verslag van die sessie wél vastligt: de rekenregels met hun bron in de spelcode, de uitkomsten van de zoektocht over ruim 5 miljoen defense/evasion-loadouts, de laganalyse van 78 wapens en de inventaris van je save. Ik heb niets opnieuw kunnen narekenen, want de spelgegevens en de simulator zijn hier niet aanwezig.

Wat dat betekent per set:

| Set | Status |
|---|---|
| 1. Hoogste Wotana | **Niet af.** Er is geen geteste build. Hieronder staat wat de ladder vraagt en welke twee halve builds er liggen. |
| 2. Maximale overleving | **Klaar als uitrusting zonder wapen.** Drie loadouts met cijfers uit de zoektocht. |
| 3. Soepel op trage pc | **Afgeleid.** Wapenkeuze en instellingen komen uit de laganalyse. De combinatie met set 2 is niet doorgerekend. |

Labels die ik gebruik:
- **[Bewezen]**: staat zo in de spelcode (f@-nummer) of in de spelgegevens (`data.cdb.json`), volgens het verslag van de vorige sessie.
- **[Berekend]**: uitkomst van de simulator van de vorige sessie. Die simulator was drie keer onafhankelijk gecontroleerd (alle 375 testgevallen slaagden), maar ik kan hem niet opnieuw draaien.
- **[Afgeleid]**: mijn conclusie uit bewezen regels, niet doorgerekend.
- **[Onbewezen]**: niet uit de spelbestanden vast te stellen. Zie `OPEN_CODEVRAGEN.md`.

## Spelregels waar elke build aan voldoet

Dit zijn jouw regels uit de overdracht, plus de spelregels die ze afdwingen.

1. **Alleen melds van hetzelfde type.** De Craftsman weigert anders: "Items must fit the same slot to meld." [Bewezen, `checkMeldConditions` f@3643]. Uitzondering: LyleCap←Amulet, LyleCloak←Book, LyleGloves←Weapon [Bewezen, f@3643 ops 152-253]. Geen van de builds hieronder gebruikt die uitzondering.
2. **Craftsman level 5** mag alles hosten behalve Offhand, Potion en Collectible [Bewezen, f@6176]. Wapens hosten vanaf level 4.
3. **meld2 alleen bij de Shaper's Anvil**, 100 hope crystals per stuk [Bewezen]. Die is in jouw save nog dicht: de Witch is niet verslagen. Daarom is elke meld2-build een aparte variant met een meld1-terugvaloptie.
4. **Geen toegevoegde blessings of actives.**
5. **q10-items die je niet hebt, staan per build onder `must_add_to_save`.** Dat is een aanname uit de overdracht: toegevoegde q10-items zijn toegestaan als ze vermeld worden. Potions kun je niet smeden [Bewezen, f@3628], dus een q10-potion is altijd toegevoegd.
6. **Schone items gebruiken.** Je huidige gemelde items dragen cross-type meld2's die de Craftsman niet kan verwijderen [Bewezen, `unmeldItem` f@3644 haalt alleen meld1 weg].
7. **Executioner's Eclipse blijft zoals hij is.**
8. De builds gaan naar Build Storage **pagina 6 tot en met 9**, die leeg zijn. Potions horen niet in Build Storage maar in de gordel [Bewezen, `equipBuild` f@10609 wisselt alleen 12 slots].

## Hoe overleven werkt (de basis voor set 1 en 2)

Alle formules hieronder zijn [Bewezen], met de bron erbij.

- **Ontwijken** (`attemptHit` f@2426): kans = e + (1−e)·se·e, met e = evasion.
- **Schade die doorkomt** (`takeHit` f@2428): je krijgt een fractie **M = damage_taken · (1−def) · (1−def·second_defense)** van de klap. Hoe kleiner M, hoe beter.
- **Defense en evasion lopen vast** op een plafond van 0,99 (`bound` f@2774, breekpunt 0,5).
- **Vijanden schalen** met difficulty D: schade en HP krijgen +0,03·D^1,65 (f@5947). Bij D110 is dat ×71, bij D800 ×1851.
- **De muurklap is het grootste gevaar.** Een Cretin-treffer slaat je tegen de muur. Die klap rekent de schade van de vijand en jouw M **een tweede keer** en negeert evasion, rollen en blokkeren (`touchWall` f@2437). Alle zeven Cretin-soorten dragen vanaf D40 de CretinHood die dit veroorzaakt.
- **Rollen zonder gat**: met roll_cooldown ≤ 0 kan tijdens het rollen niets je raken. Legaal haalbaar met Pattens+AcrobatSlippers, Salto en LastPrinciples (samen −0,2). Nadeel: tijdens het rollen kun je niet aanvallen of blokkeren.

Dat laatste punt over de muurklap is waarom evasion alleen niet genoeg is. Een build met 98% ontwijking en 136 HP gaat dood aan de eerste Cretin die wél raakt.

---

## Set 1: hoogst haalbare Wotana

**Status: niet af. Er is geen build die ik kan onderbouwen.**

### Hoe de ladder werkt [Bewezen, `completeDelve` f@3240 en `failDelve` f@3241]

Wotana (gebied 7, "Path of Wotana") zit achter de Wotana-deur in Gates of Despair. De sleutel valt bij het verslaan van de Witch. **Die heb je nog niet verslagen, dus Wotana is nog niet open.**

Elke gewonnen run maakt de volgende zwaarder:

| Run | Difficulty | Daarna |
|---|---|---|
| 1 | 110 | 120 |
| 2 | 120 | 140 |
| 3 | 140 | 260 |
| 4 | 260 | 480 |
| 5 | 480 | 800 |
| 6 | 800 | 1220 |
| 7 | 1220 | 1740 |
| 8 | 1740 | 2360 |

Eén verlies kost de hele reeks: daarna stijg je weer met +10 per winst. Stoppen via "Return to Menu" of "Quit Game" telt niet als verlies [Bewezen, f@5709/f@5710], maar wat "Continue" daarna doet is [Onbewezen]. Doodgaan in de TempleHope na de baas telt als winst [Bewezen, f@7787].

Een run heeft 12 gevechtsniveaus en eindigt met een van 10 bazen, willekeurig gekozen [Bewezen, f@3236, f@3248]. Encounters zoals RatsNest en CowardsBridge zijn altijd te vermijden door de andere deur te kiezen [Bewezen, f@3249].

### Wat elke trede vraagt [Berekend]

- Baas-HP: 0,87 miljoen bij D260, 2,39 miljoen bij D480, 5,55 miljoen bij D800, 11,1 miljoen bij D1220.
- Om bij D800 de baas te overleven heb je ongeveer M ≤ 0,003, ontwijkkans rond 0,86 en minstens 50.000 DPS nodig. Tegen LastRemnant minstens 100.000.
- Bij D1220 vragen de meeste bazen rond 300.000 DPS.
- Instant kill (ExplodingHeart, maximaal 0,2024) werkt op 9 van de 10 bazen, niet op Anguished [Bewezen, f@5951, f@6149].

### Wat er ligt

**Helft 1: kill-kern K1b** [Berekend, alle melds meld1 en legaal]
ExecutionersAxe←Razorice, MonstersGuide←SavageDictolydium, FertilityGarland←Spectacles, Icestrike←PlateBoots, Shattertips←ExplodingHeart. Elke treffer bevriest, 20,7% kans per treffer om een bevroren gewone vijand direct te doden, ongeacht D. Gemiddeld 3,2 seconden voor een Colossus. Bazen moet je onder 79,8% HP krijgen, dan pakt instant kill ze.

**Helft 2: een verdedigingskern uit set 2** (zie hieronder).

**Het probleem:** beide helften willen dezelfde helm, handschoenen, laarzen en boek. Welke combinatie het hoogst komt, moet de simulator uitrekenen. Dat kon ik niet. Een schatting zou gokwerk zijn en dat wil je niet.

**Wat ik wel kan zeggen [Afgeleid]:** met de beste verdediging die meld1 toelaat (M 0,006, zie 2A) haal je de M ≤ 0,003 voor D800 niet. Zonder Shaper's Anvil is D480 → 800 (run 5 winnen) de realistische grens. Dat is een conclusie uit de tabellen, geen doorgerekende build.

---

## Set 2: maximale overleving

Deze drie loadouts komen uit de uitputtende zoektocht van de vorige sessie: alle legale same-type melds per slot, per doel. De wapenslot is in alle drie vrij; de zoektocht keek alleen naar verdediging.

**Belangrijk:** alle drie leunen op een q10-**Melancholic** in gordelslot 1, die daar ongedronken blijft staan. Die heb je niet, in geen enkele kwaliteit. Zonder die potion gelden de cijfers niet. De versies zonder gordel zijn wel doorzocht, maar die resultaten staan niet volledig in het verslag.

Drink die potion niet per ongeluk. De gordel vult een leeg slot eerst aan met een Health-phial uit je tas [Bewezen, f@10570], en dan is het effect weg.

### 2A "Bolwerk": meeste HP, best tegen de muurklap (meld1)

[Berekend, zoekdoel C, plaats 1]

| Slot | Host ← meld |
|---|---|
| Helm | FertilityGarland ← Spectacles |
| Harnas | LeofgarPlate ← Witchichor |
| Handschoenen | DandyGloves ← OrnamentalRing |
| Laarzen | LeoGreaves ← Winklepickers |
| Boek | Diary ← SavageDictolydium |
| Amulet | WiseSpirit ← SeraVessel |
| Runes (4×) | SeraLight ← PotentReagent |
| Offhand | KiteShield |
| Gordel 1 | Melancholic q10 |

HP 1307, defense 0,9889, M 0,00639, evasion 0. Overleeft één klap tot D1890 en een Colossus-treffer plus muurklap tot D665. Nadeel: gedronken buffs duren vrijwel nul seconden (PotentReagent).

### 2B "Schim": defense én evasion (meld1)

[Berekend, zoekdoel B, plaats 3]

| Slot | Host ← meld |
|---|---|
| Helm | CowelRhys ← FertilityGarland |
| Harnas | LeofgarPlate ← Witchichor |
| Handschoenen | LeatherMittens ← OrnamentalRing |
| Laarzen | Winklepickers ← Mandoletinas |
| Boek | Diary ← SavageDictolydium |
| Amulet | SeraVessel ← WiseSpirit |
| Runes (4×) | PotentReagent ← SeraLight |
| Offhand | LeoSlab |
| Gordel 1 | Melancholic q10 |

HP 440, defense 0,9892, evasion 0,716, M 0,00618. Overleeft één klap tot D990 en klap plus muurklap tot D473. Dit is het antwoord op "hoge defense met hoge evasion" zonder Shaper.

Mandoletinas moet de **meld** zijn, niet de host: als host zet hij defense op 0. In de zoekresultaten stond het paar als "Mandoletinas+Winklepickers"; de volgorde van host en meld is in die notatie niet eenduidig. Zie open vraag 16.

### 2C "Schim+" Shaper-variant: het hoogste van allebei (meld2)

[Berekend, zoekdoel E gebalanceerd, meld2, plaats 1]

| Slot | Host + meld + meld2 |
|---|---|
| Helm | CowelRhys + FertilityGarland + Spectacles |
| Harnas | GambesonRhys + LeofgarPlate + Witchichor |
| Handschoenen | IronMittens + LeatherMittens + OrnamentalRing |
| Laarzen | Stompers + Mandoletinas + Winklepickers |
| Boek | Diary + JoyLife + SavageDictolydium |
| Amulet | GhostPendant + SeraVessel + WiseSpirit |
| Runes (4×) | AssRune + PotentReagent + SeraLight |
| Offhand | KiteShield |
| Gordel 1 | Melancholic q10 + meld2 Quicksilver |

Defense 0,9899, evasion 0,9897, ontwijkkans 0,994, M 0,00578, HP 548. Overleeft één klap tot D1181 en klap plus muurklap tot D532. Nadeel: snelheid en aanvalssnelheid ×0,655.

Dit kost **15 meld2's = 1500 hope crystals**, precies wat je hebt. Werkt pas na de Witch. Tot die tijd: 2B.

---

## Set 3: soepel op een trage pc

### Waarom het spel hapert [Bewezen, laganalyse]

- Elk aanvalsvak (hitbox) dat je aanmaakt wordt elk frame tegen alle andere objecten getest. Overlappende melee-vakken kosten kwadratisch [f@4814, f@4812].
- Alle vakken van een aanvalsreeks blijven bestaan tot de laatste verloopt [f@5906, f@5907].
- "Hit Stutter" is een bewuste bevriezing per treffer, tot 0,2 seconde bij crits [f@3386]. Jouw save staat op het maximum.

De lagscore in de analyse is een **model**, geen meting. Hij is bedoeld om wapens te rangschikken.

### Instellingen [Bewezen]

| Instelling | Nu | Zet op |
|---|---|---|
| Hit Stutter | 1 | **0** |
| Damage popups | aan | **uit** |
| CRT | aan | **uit** |
| Lighting | aan | aan laten (uit lekt geheugen) |
| Vsync | aan | aan laten |

Mogelijk de grootste winst: het spel opent op het 144 Hz-scherm van je laptop, dat door de AMD-iGPU wordt aangestuurd. Of het spel daar ook op rendert is [Onbewezen]. Probeer in de Windows-instellingen bij Beeldscherm > Graphics de RTX (hoge prestaties) in te stellen voor Necrovale.exe, of speel op het 60 Hz-scherm.

### Wapenkeuze [Berekend, onder de crit-uitrusting van de oude Bloodbeam-build]

| Wapen | DPS (1 doel) | Objecten per klik | Lagscore |
|---|---|---|---|
| VanceDagger ← Heirloom | 22.757 | 1, ook bij power | 21 |
| Heirloom (ongemeld) | 23.175 | 1 normaal, 2 bij power | 15 / 448 |
| ExecutionersAxe ← Heirloom | 21.267 | 1 | 18 / 28 |
| CleghornsBlock ← Heirloom | 20.066 | 1 (power: één 360°-vak) | 28 / 37 |

63 van de 78 wapens maken bij een normale klik hooguit één object.

**Vermijden**, want ze vermenigvuldigen objecten: ThirdEye, Redoublers, GoldenFingernail, Eyeball, MirroredLocket, ChainLightning, GrenadierGloves, SteeleyeCirclet, CrownOfStorms, de offhands Bloodshriek, NowhereWand en KnaveHearts, en de power-aanvallen van RainTears, ShockSticker en HammerWotana. Singularities is het enige legale item dat objecten vermindert.

### 3A "Licht Bolwerk"

Uitrusting van **2A** met **VanceDagger ← Heirloom** als wapen.

[Afgeleid] Geen enkel item in 2A staat op de vermijdlijst, en 2A voegt geen extra aanvallen toe, dus de lagscore van het wapen (21) blijft gelden. De DPS hierboven is gemeten met andere uitrusting. Met 2A is je aanvalssnelheid lager, dus reken op minder. Hoeveel minder heb ik niet kunnen narekenen.

---

## Wat je moet toevoegen of vrijmaken

Volgens de inventaris van de vorige sessie [Bewezen uit je save van 8 oktober]:
- 47.313 munten en 1500 hope crystals.
- 25 smeedbeurten met EmberGods. Eén volledige build vanaf q0 kost er tot 23.
- **Niet in je bezit**: Melancholic, Quicksilver (geen enkele q10-potion).
- **Vast in een meld2** (alleen de Shaper krijgt ze los): Diary, LeoGreaves, SeraLight, DogRune, Icestrike en zes andere.
- Heirloom zit in de meld Heirloom+Bloodletter op pagina 4. Een gratis split bij de Craftsman haalt hem terug.

De lijst `must_add_to_save` in `builds.json` bevat alleen wat ik zeker weet. Voor de rest van de items had ik de volledige eigendomstabel nodig, en die is weg. Controleer dus vóór het wegschrijven met de save zelf.

Volg bij elke save-wijziging de werkwijze uit de overdracht: spel dicht, back-up van `slot1.sav` en `slot1.prev.sav`, en kies bij een Steam Cloud-conflict de lokale versie.

## Wat er nodig is om set 1 af te maken

1. De zip `Necrovale_1_overdracht_onderzoek_tools.zip` opnieuw uploaden (bevat `data.cdb.json`, de codedumps en de save).
2. De simulator opnieuw opbouwen. Daar is een aparte taak voor in dit project.
3. Kill-kern en verdedigingskern combineren en per trede van de ladder doorrekenen.
