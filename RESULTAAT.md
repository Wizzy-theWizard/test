# Into the Necrovale: acht builds

Stand: 10 oktober 2026. Game build 20114049. Berekend met de opnieuw opgebouwde simulator en jouw spelbestanden (speldata, spelcode, save van 8 oktober).

## In het kort

Je vroeg om vier builds met 2 melds en daarna dezelfde vier met 3 melds, allemaal bijna niet dood te krijgen:

| Doel | 2 melds (nu te bouwen) | 3 melds (pas na de Heks) |
|---|---|---|
| Zo min mogelijk stotteren (focus) | **A1 Stille Dolk** | **A2 Stille Dolk+** |
| Heel het scherm vernietigen | **B1 Vuurzee** | **B2 Vuurzee+** |
| Vijanden zo snel mogelijk dood | **C1 Bloedstraal-beul** | **C2 Bloedstraal-beul+** |
| Lui: zoekende projectielen, stilstaan | **D1 IJsjager** | **D2 IJsjager+** |

Alle acht zijn legaal: elke meld is een Craftsman-meld van hetzelfde type, de derde meld komt van de Shaper, en de Executioner's Eclipse blijft onaangeroerd.

Vier dingen moet je weten voordat je kiest:

1. **De meeste onderdelen heb je niet.** Per build moeten 17 tot 24 onderdelen in je save worden toegevoegd (q10). Dat doet Claude Code op je pc, met back-ups. Je bestaande build-pagina's 1 tot en met 5 blijven heel, tenzij je zegt dat er onderdelen uit mogen.
2. **Er zijn 5 vrije pagina's (6 tot en met 10) voor 8 builds.** Je kiest er dus maximaal 5, of je laat oude pagina's overschrijven.
3. **3 melds kan pas na de Heks.** Daarvoor moet je nog door de River-deur (77 HC), twee zegels, 9 Witch Trials en de Heks zelf. Alle vier de 3-meld-builds samen kosten 1.400 HC; na de River-deur heb je er 1.423.
4. **Muurhoeken zijn voor elke build het grootste gevaar.** Een Colossus die je in een hoek slaat, kan meerdere muurklappen achter elkaar geven, en die gaan door ontwijken heen. Met 2 melds overleef je een klap plus 2 muurklappen maar tot ongeveer D83. Zie "Colossus en muurhoeken" hieronder.

## Keuzetabel

| Build | Overleving S (met / zonder riem) | Muurhoek b2 | Blok houdt tot | Heks op D100 | Lag (model) | HC | Uit save erbij |
|---|---|---|---|---|---|---|---|
| A1 Stille Dolk | D143 / D143 | D89 | D114 | 10,7 s | 21 | 0 | 18 |
| A2 Stille Dolk+ | D176 / D176 | D137 | D129 | 6,5 s | 21 | 300 | 20 |
| B1 Vuurzee | D152 / **D60** | D96 / D30 | geen blok | 22,5 s | 164 tot 422 | 0 | 21 |
| B2 Vuurzee+ | D206 / D111 | D167 / D61 | geen blok | 16,7 s | 164 tot 422 | 300 | 3 bovenop B1 |
| C1 Bloedstraal-beul | D141 / D141 | D84 | geen blok | 8,8 s | 334 | 0 | 19 |
| C2 Bloedstraal-beul+ | D166 / D166 | D112 | D114 | 2,8 s | 431 | 400 | 21 |
| D1 IJsjager | D150 / D150 | D83 | D92 | 3,3 tot 5,9 s | 488, altijd | 0 | 17 |
| D2 IJsjager+ | D212 / D212 | D153 | D188 | 0,5 s | 1.370, altijd | 400 | 22 |

Zo lees je de kolommen:

- **Overleving S** [berekend]: de hoogste moeilijkheid waarop je elke losse zware aanval overleeft vanaf volle HP. Getest zijn een Popspore-elite, Colossus-klap plus muurklap, Crusher-klap plus muurklap, Goatman-dash, LastRemnant-salvo en PestSlime-spuug. Het laagste getal telt, naar beneden afgerond. Jouw save staat nu op moeilijkheid 41, de Heks is D100 en Wotana begint op D110.
- **Muurhoek b2** [berekend]: hetzelfde voor 1 Colossus-klap plus 2 muurklappen direct achter elkaar. Dat gebeurt als je in een hoek of tegen een naad tussen twee muurstukken wordt geslagen.
- **Blok houdt tot** [berekend]: tot deze moeilijkheid breekt een Colossus-klap je poise niet als je blokt. Dan word je niet weggeslagen en komt er ook geen muurklap.
- **Heks op D100** [berekend]: hoe lang je erover doet om haar 2 HP-balken weg te slaan als alles raakt.
- **Lag** [model]: een rekenmodel voor hoeveel objecten en deeltjes de build per seconde maakt. Lager is rustiger. De gewichten in het model zijn niet gemeten; alleen het aantal objecten is uit de code bewezen. Hoeveel fps je echt haalt, moet je in het spel testen.
- **Uit save erbij** [berekend]: hoeveel onderdelen in je save moeten als je deze build als enige bouwt. Je eigen losse stash-items zijn al meegeteld; pagina's 1 tot en met 5 en de Eclipse niet. Bouw je meerdere builds, dan stijgt dit, want elk stash-item kan maar op 1 pagina.

## Wat voor alle builds geldt

### Knoppen met jouw instellingen [bewezen]

In jouw `settings.sav` staat de power-aanval op de **linkermuisknop** en de gewone aanval op de **middelste muisknop**. De **rechtermuisknop** is je offhand: blokken met een schild, rollen met Salto. Een knop ingedrukt houden herhaalt de aanval vanzelf.

- A: middelste knop (gewone steek, 34.793 DPS) is iets sterker dan links (34.146). Allebei goed.
- B: links of midden. Midden geeft het minste lag.
- C: alleen links. Dat is precies de krachtaanval die deze build nodig heeft.
- D: niet klikken. Links maakt 28 objecten per klik en kost veel lag. Rechts vasthouden (blok) mag altijd.

### Instellingen tegen stotteren

- **Hit Stutter op 0** [bewezen]: dan pauzeert het spel helemaal niet meer bij een treffer. Nu staat hij op 1.
- **Popups uit** [bewezen]: schadegetallen worden dan niet meer gemaakt. Een paar teksten blijven altijd, zoals "Evade" en "Executed".
- **CRT uit** en **vsync aan** laten tegen screen tearing. Dit is advies; het effect is niet gemeten.
- **Videokaart** [onbewezen]: het spel opent nu op je 144 Hz-scherm, dat aan de AMD-chip in je processor hangt. In Windows kun je bij Instellingen > Systeem > Beeldscherm > Graphics voor Necrovale.exe "Hoge prestaties" kiezen. Of het spel dan op de RTX 4070 draait, valt niet uit de spelcode af te leiden. Probeer het en kijk of het verschil maakt.

### Colossus en muurhoeken

Wordt je poise gebroken, dan vlieg je weg. Raak je een muur, dan volgt een muurklap die de klap van de vijand nog een keer laat aankomen en die niet te ontwijken, te blokken of weg te rollen is [bewezen]. Muren zijn grote rechthoeken, dus langs een rechte muur glijden geeft geen reeks klappen. Elke nieuwe muurrechthoek die je in dezelfde vlucht raakt, geeft wel een nieuwe klap, en die wordt steeds zwaarder [bewezen].

Wat dat betekent [afgeleid]:

- Tot ongeveer D83 overleeft elke build (met riem) een Colossus-klap plus 2 muurklappen. Drie of meer muurklappen kan ook en is nog zwaarder: bij C1 gaat dat al vanaf D63 mis.
- Daarboven: vecht niet met je rug tegen een muur of in een hoek, en blok of rol zodra een Colossus uithaalt.
- A1, A2, C2 en D2 kunnen de klap op D110 opvangen met hun blok. C1 en B kunnen niet blokken. Bij D1 houdt het blok maar tot D92.

### De riem

- De riem hoort niet bij een Build Storage-pagina. Wat erin zit, geldt voor alle pagina's tegelijk [bewezen].
- Je 4 HealthLarge-drankjes (q1) genezen elk 90 HP [bewezen]. Bij B is dat 331 HP, omdat B je drankjes 3,7 keer sterker maakt.
- Alleen B gebruikt riemvak 1 voor een Melancholic (q10). Die heb je niet; hij moet in de save. Bij B nooit toets 1 indrukken: drinken haalt hem weg en het effect is dan nul. Kies je B, dan staat die Melancholic ook op A, C en D in vak 1. Daar doet hij niets, maar toets 1 drinkt hem wel op.

### Embers

Sommige amuletten zetten de kans op willekeurige embers van vijanden lager [berekend]:

- **Geen willekeurige embers:** A1, A2, B2, D1 en D2.
- **10% van normaal:** B1 en C2.
- **Normaal:** C1.

Je 25 Ember of the Gods-gebruiken in voorraad blijven werken.

### Naar de Shaper (nodig voor de 3-meld-builds)

De route uit jouw save [bewezen]:

1. River-deur: 77 HC.
2. River, dan het Seal of Ire (moeilijkheid 30).
3. Palace, dan het Seal of Fear (moeilijkheid 50).
4. Terug naar de Refuge.
5. 9 Witch Trials, dan de Heks. Ze heeft 2 HP-balken en is te verslaan.
6. Uit haar beloningskist komt de ShapersKey. Daarna kost elke derde meld 100 HC.

**Pas op bij stap 4** [bewezen]: zodra alle 5 zegels gebroken zijn, slaat het spel meteen op en gaat de laatste deur pas 2,5 seconde later open. Stop je het spel in die paar seconden of crasht het, dan blijft die deur dicht. Wacht in de Refuge minstens 10 seconden tot de deur open is, en ga daarna pas weg.

### Waar het niet tegen kan

Geen enkele build overleeft 10 minuten aanhoudend vuur zonder genezing [berekend]. A2 en D2 houden dat tot D19 vol, de rest zelfs D10 niet. Blijf dus niet in eindeloos vuur staan en drink op tijd.

---

## A1 Stille Dolk (2 melds)

**Voor:** zo min mogelijk stotteren. Dit is je focus-build.

**Zo speel je hem.** Loop naar de vijanden toe en steek. Ongeveer 6 steken per seconde, en elke steek is precies 1 klein raakvlak. Er zijn geen projectielen, explosies, brand, ijs of executies. Je ontwijkt 86% van de aanvallen en houdt 94% defense. Elke kill geeft 3,8 x de waarde van de vijand aan HP terug. Houd rechts vast (blok) als een Colossus uithaalt.

| Slot | Host | Meld | Meld2 |
|---|---|---|---|
| Weapon | VanceDagger | Heirloom | |
| Offhand | BulwarkShield | | |
| Amulet | GhostPendant | HeartGreed | |
| Book | Einkorn | SavageDictolydium | |
| Helmet | CowelRhys | LeofgarCasque | |
| Armor | Battlepriest | ShrunkenTunic | |
| Boots | Stompers | Mandoletinas | |
| Gloves | LeatherMittens | PlateGloves | |
| Rune1 | SeraLight | SnakeRune | |
| Rune2 | SeraLight | SnakeRune | |
| Rune3 | SeraLight | WormRune | |
| Rune4 | ImperialCoin | SnakeRune | |

Riem: 4x HealthLarge, zoals nu. Deze build heeft geen riem nodig.

- **Overleving** [berekend]: 1.025 HP, defense 0,944, ontwijken 86%. S = D143 (zwakste punt: PestSlime-spuug). Muurhoek b2 D89. Blok houdt tot D114. De straal van de Heks overleef je helemaal.
- **Schade** [berekend]: 34.793 DPS met de middelste knop, 34.146 met links. Heks 10,7 s.
- **Lag** [model]: 1 object per steek, score 21. De rustigste van alle acht.
- **Kosten**: 0 HC, 3.580 munten bij de Craftsman, 3 Ember-gebruiken (BulwarkShield, ShrunkenTunic en LeatherMittens uit je stash naar q10).
- **Uit de save erbij (18):** VanceDagger, Heirloom, HeartGreed, Einkorn, SavageDictolydium, CowelRhys, LeofgarCasque, Battlepriest, Stompers, Mandoletinas, PlateGloves, 3x SeraLight, 3x SnakeRune, WormRune.
- **Let op:** je loopt op 70% snelheid. Melee, dus je moet dichtbij staan (35 px). Geen willekeurige embers.

## A2 Stille Dolk+ (3 melds)

**Voor:** zo min mogelijk stotteren, met meer schade en overleving. Pas na de Heks.

**Zo speel je hem.** Precies als A1. Het boek laat gewone vijanden starten op 78,7% HP, zonder extra objecten of tekst.

| Slot | Host | Meld | Meld2 |
|---|---|---|---|
| Weapon | VanceDagger | Heirloom | |
| Offhand | KiteShield | | |
| Amulet | GhostPendant | HeartGreed | GuidingSpirit |
| Book | SavageDictolydium | MonstersGuide | |
| Helmet | CowelRhys | LeofgarCasque | FertilityGarland |
| Armor | Battlepriest | ShrunkenTunic | PlateArmor |
| Boots | Stompers | Mandoletinas | |
| Gloves | LeatherMittens | PlateGloves | |
| Rune1 | SeraLight | SnakeRune | |
| Rune2 | SeraLight | SnakeRune | |
| Rune3 | SeraLight | WormRune | |
| Rune4 | ImperialCoin | SnakeRune | |

Riem: 4x HealthLarge.

- **Overleving** [berekend]: 1.025 HP, defense 0,970, ontwijken 88%. S = D176. Muurhoek b2 D137. Blok houdt tot D129.
- **Schade** [berekend]: 57.643 DPS midden, 56.500 links; tegen gewone vijanden effectief 63.705 door de lagere start-HP. Heks 6,5 s.
- **Lag** [model]: score 21, gelijk aan A1.
- **Kosten**: 300 HC, 3.620 munten, 4 Ember-gebruiken.
- **Uit de save erbij (20):** VanceDagger, Heirloom, HeartGreed, SavageDictolydium, MonstersGuide, CowelRhys, LeofgarCasque, FertilityGarland, Battlepriest, PlateArmor, Stompers, Mandoletinas, PlateGloves, 3x SeraLight, 3x SnakeRune, WormRune.
- **Let op:** dit is een eigen pagina met eigen onderdelen, geen upgrade van A1. Loopsnelheid 65,5%. Geen willekeurige embers.

## B1 Vuurzee (2 melds)

**Voor:** heel het scherm vernietigen.

**Zo speel je hem.** Gooi speren naar de dichtste groep. Elke treffer zet met 70% kans een vijand in brand. Elke brandende vijand, ook een dode, steekt elke 0,2 s de volgende vijand binnen 468 px aan. Vanuit het midden is dat je hele 1080p-beeld [afgeleid]. Jij ontsteekt af en toe opnieuw en blijft rollen. Rol meteen uit groen PestSlime-spuug.

| Slot | Host | Meld | Meld2 |
|---|---|---|---|
| Weapon | Javelin | FlameColumnStaff | |
| Offhand | Salto | | |
| Amulet | ElementalWhirlwind | HeartGreed | |
| Book | SavageDictolydium | SeraBook | |
| Helmet | BalorMask | Spectacles | |
| Armor | ThrallsPlate | Witchichor | |
| Boots | LeoGreaves | PlateBoots | |
| Gloves | IronMittens | TrickReach | |
| Rune1 | LizardRune | PotentReagent | |
| Rune2 | PotentReagent | SnakeRune | |
| Rune3 | LizardRune | PotentReagent | |
| Rune4 | PotentReagent | SnakeRune | |

Riem: **vak 1 Melancholic (q10)**, vak 2 tot 4 HealthLarge.

- **Overleving met Melancholic** [berekend]: 1.160 HP, defense 0,947, geen ontwijken. S = D152. Muurhoek b2 D96.
- **Overleving zonder Melancholic** [berekend]: S = **D60** en de straal van de Heks doodt je na 5 tikken. Zonder die save-toevoeging is B1 dus niet "bijna niet dood".
- **Schade** [berekend]: elke brandende vijand krijgt 3.134 schade per 0,2 s (15.669 DPS). Op D110 is 78% van de vijandsoorten uit de speldata binnen 1 seconde dood (ongewogen geteld). Heks 22,5 s.
- **Lag** [model]: 1 actieve speer per worp; brand maakt geen objecten. Score 164 (midden) of 422 (links). Hoeveel rekenwerk honderden brandende vijanden kosten, is niet gemeten.
- **Kosten**: 0 HC, 3.480 munten, 3 Ember-gebruiken (Javelin, TrickReach en PotentReagent uit je stash).
- **Uit de save erbij (21):** FlameColumnStaff, Salto, ElementalWhirlwind, HeartGreed, SavageDictolydium, SeraBook, BalorMask, Spectacles, ThrallsPlate, Witchichor, LeoGreaves, PlateBoots, IronMittens, 2x LizardRune, 3x PotentReagent, 2x SnakeRune, Melancholic.
- **Let op:** geen blok en geen genezing per kill. Ontwijkende vijanden ontwijken ook brandtikken. Embers op 10%.
- **Wil je geen Melancholic?** Er is een variant zonder riem-afhankelijkheid (S D151 met en zonder riem, 86% ontwijken), maar het vuur is veel zwakker: 945 per tik, bereik 376 px, Heks 70,7 s. Die variant is niet opnieuw nagerekend.

## B2 Vuurzee+ (3 melds)

**Voor:** heel het scherm vernietigen, en ook zonder riem redelijk veilig. Pas na de Heks.

**Zo speel je hem.** Precies als B1. Dit is de enige 3-meld-build die een echte upgrade is: je meldt 3 extra onderdelen op de B1-pagina zelf.

| Slot | Host | Meld | Meld2 |
|---|---|---|---|
| Weapon | Javelin | FlameColumnStaff | |
| Offhand | Salto | | |
| Amulet | ElementalWhirlwind | HeartGreed | |
| Book | SavageDictolydium | SeraBook | |
| Helmet | BalorMask | Spectacles | BeautifulArmet |
| Armor | ThrallsPlate | Witchichor | LeofgarPlate |
| Boots | LeoGreaves | PlateBoots | Winklepickers |
| Gloves | IronMittens | TrickReach | |
| Rune1 | LizardRune | PotentReagent | |
| Rune2 | PotentReagent | SnakeRune | |
| Rune3 | LizardRune | PotentReagent | |
| Rune4 | PotentReagent | SnakeRune | |

Riem: vak 1 Melancholic, vak 2 tot 4 HealthLarge.

- **Overleving** [berekend]: 1.376 HP, defense 0,961 plus second defense 0,375. Met Melancholic S = D206, muurhoek b2 D167. Zonder S = D111, b2 D61.
- **Schade** [berekend]: 4.268 per tik (21.340 DPS per brandende vijand). Op D110 is 87% van de vijandsoorten uit de speldata binnen 1 s dood (ongewogen geteld). Heks 16,7 s.
- **Lag** [model]: gelijk aan B1.
- **Kosten**: 300 HC. Als upgrade van B1: BeautifulArmet, LeofgarPlate en Winklepickers erbij. Als aparte pagina: alles van B1 nog een keer plus die 3 (24 in totaal).
- **Let op:** BeautifulArmet verlaagt je maximale poise (275 in plaats van 387), maar door de extra defense breekt de Colossus hem pas vanaf D11 in plaats van D5. Geen blok. Geen willekeurige embers.

## C1 Bloedstraal-beul (2 melds)

**Voor:** vijanden zo snel mogelijk dood, actief spelen.

**Zo speel je hem.** Houd links ingedrukt. Elke krachtklik is een zware zwaai plus een BloodBeam-straal die door vijanden heen gaat (356 px). Een krachtklik kost 3 kracht; elke executie vult de balk weer met 9 x de waarde van de vijand. Is de balk leeg, dan doet links een gewone klap. Sta dicht op de vijand (zwaai 49 px). Je hebt geen blok: rol weg zodra een Colossus uithaalt.

| Slot | Host | Meld | Meld2 |
|---|---|---|---|
| Weapon | Heirloom | | |
| Offhand | Salto | | |
| Amulet | BaltairMillstone | GuillameSoultrap | |
| Book | Diary | SavageDictolydium | |
| Helmet | CowelRhys | FertilityGarland | |
| Armor | ShrunkenTunic | ThrallsPlate | |
| Boots | LeatherBoots | LeoGreaves | |
| Gloves | LeatherMittens | PlateGloves | |
| Rune1 | GuillameThoughtvoid | SnakeRune | |
| Rune2 | DogRune | GuillameThoughtvoid | |
| Rune3 | GuillameThoughtvoid | SnakeRune | |
| Rune4 | GuillameThoughtvoid | WormRune | |

Riem: 4x HealthLarge. Deze build heeft geen riem nodig.

- **Overleving** [berekend]: 1.088 HP, defense 0,938, ontwijken 81%. S = D141. Muurhoek b2 D84. Geen blok.
- **Schade** [berekend]: 41.427 DPS zolang executies de balk vullen; zonder hervulling 9.409. Baas op D110: 5,1 s (zonder hervulling 22,7 s). Heks 8,8 s.
- **Lag** [model]: 2 objecten per krachtklik, score 334. Daarnaast gemiddeld 3,7 keer per seconde de tekst "Executed", die niet uit kan.
- **Kosten**: 0 HC, 3.180 munten, 3 Ember-gebruiken (ShrunkenTunic, LeatherBoots en LeatherMittens uit je stash).
- **Uit de save erbij (19):** Heirloom, Salto, BaltairMillstone, GuillameSoultrap, Diary, SavageDictolydium, CowelRhys, FertilityGarland, ThrallsPlate, LeoGreaves, PlateGloves, 4x GuillameThoughtvoid, 2x SnakeRune, DogRune, WormRune.
- **Let op:** DemonicMarquess vult de balk niet (waarde 0); reken daar met de tijden zonder hervulling. Embers normaal.

## C2 Bloedstraal-beul+ (3 melds)

**Voor:** vijanden zo snel mogelijk dood. Pas na de Heks.

**Zo speel je hem.** Als C1, maar deze basis heeft een KiteShield: op D110 kun je de Colossus-klap blokken.

| Slot | Host | Meld | Meld2 |
|---|---|---|---|
| Weapon | Heirloom | | |
| Offhand | KiteShield | | |
| Amulet | GuillameSoultrap | HeartGreed | GuidingSpirit |
| Book | Einkorn | SavageDictolydium | |
| Helmet | CowelRhys | FertilityGarland | Spectacles |
| Armor | ShrunkenTunic | ThrallsPlate | Battlepriest |
| Boots | LeatherBoots | LeoGreaves | PlateBoots |
| Gloves | IronMittens | LeatherMittens | |
| Rune1 | GuillameThoughtvoid | SnakeRune | |
| Rune2 | GuillameThoughtvoid | SnakeRune | |
| Rune3 | GuillameThoughtvoid | SnakeRune | |
| Rune4 | GuillameThoughtvoid | WormRune | |

Riem: 4x HealthLarge.

- **Overleving** [berekend]: 1.232 HP, defense 0,957, ontwijken 81%. S = D166. Muurhoek b2 D112. Blok houdt tot D114.
- **Schade** [berekend]: 130.819 DPS met hervulling, 41.546 zonder. Baas op D110: 1,6 s (zonder hervulling 5,1 s). Heks 2,8 s.
- **Lag** [model]: score 431 en gemiddeld 5,6 keer per seconde "Executed".
- **Kosten**: 400 HC, 3.240 munten, 5 Ember-gebruiken.
- **Uit de save erbij (21):** Heirloom, GuillameSoultrap, HeartGreed, Einkorn, SavageDictolydium, CowelRhys, FertilityGarland, Spectacles, ThrallsPlate, Battlepriest, LeoGreaves, PlateBoots, IronMittens, 4x GuillameThoughtvoid, 3x SnakeRune, WormRune.
- **Let op:** eigen pagina, geen upgrade van C1. Embers op 10%.

## D1 IJsjager (2 melds)

**Voor:** lui spelen met zoekende projectielen.

**Zo speel je hem.** Ga stilstaan en klik niet. De helm vuurt elke 0,2 s 2 ijsbitjes af [bewezen], ook als er geen vijand is. Die sturen zelf bij naar de vijand die het dichtst bij jou staat. Ze vliegen maar ongeveer 51 px ver: laat vijanden naar je toe komen, en loop een stukje naar schutters die verder weg blijven.

| Slot | Host | Meld | Meld2 |
|---|---|---|---|
| Weapon | Heirloom | | |
| Offhand | KiteShield | | |
| Amulet | ThirdEye | HeartGreed | |
| Book | Diary | SavageDictolydium | |
| Helmet | CowelRhys | CrownArrogance | |
| Armor | ShrunkenTunic | ThrallsPlate | |
| Boots | Stompers | Mandoletinas | |
| Gloves | LeatherMittens | Heartseek | |
| Rune1 | BoarRune | SeraLight | |
| Rune2 | SnakeRune | SeraLight | |
| Rune3 | DogRune | SeraLight | |
| Rune4 | BoarRune | SeraLight | |

Riem: 4x HealthLarge.

- **Overleving** [berekend]: 1.476 HP, defense 0,930, ontwijken 80%. S = D150. Muurhoek b2 D83. Blok houdt maar tot D92. Kills met ijsbitjes genezen niet.
- **Schade**: elk bitje doet 11.009 schade [berekend]. Raken alle bitjes, dan is dat 110.086 DPS [berekend; bij 60 fps 101.618]. Het trefmodel schat dat tegen een stilstaande vijand dichtbij gemiddeld 56% raakt: 61.873 DPS [model]. Tegen bewegende vijanden en met muren is dat niet doorgerekend. Heks 3,3 s als alles raakt, 5,9 s met het model.
- **Lag** [model]: geen low-lag build. Score 488, de hele tijd.
- **Kosten**: 0 HC, 3.180 munten, 5 Ember-gebruiken (KiteShield, CrownArrogance, ShrunkenTunic, LeatherMittens en Heartseek uit je stash).
- **Uit de save erbij (17):** Heirloom, ThirdEye, HeartGreed, Diary, SavageDictolydium, CowelRhys, ThrallsPlate, Stompers, Mandoletinas, 2x BoarRune, 4x SeraLight, SnakeRune, DogRune.
- **Let op:** loopsnelheid 70%. Geen willekeurige embers.

## D2 IJsjager+ (3 melds)

**Voor:** echt lui spelen. Pas na de Heks.

**Zo speel je hem.** Stilstaan en niet klikken. De bitjes vliegen nu 145 px en zoeken veel sterker; in het model raken ze alles tot 100 px. Rechts vasthouden (blok) mag altijd.

| Slot | Host | Meld | Meld2 |
|---|---|---|---|
| Weapon | Heirloom | | |
| Offhand | KiteShield | | |
| Amulet | ThirdEye | HeartGreed | CobraNecklace |
| Book | Diary | SavageDictolydium | |
| Helmet | CowelRhys | CrownArrogance | LeofgarCasque |
| Armor | ShrunkenTunic | LeofgarPlate | HeavyIron |
| Boots | Stompers | Mandoletinas | LeoGreaves |
| Gloves | LeatherMittens | IronMittens | |
| Rune1 | SnakeRune | SeraLight | |
| Rune2 | SnakeRune | SeraLight | |
| Rune3 | DogRune | SeraLight | |
| Rune4 | SnakeRune | SeraLight | |

Riem: 4x HealthLarge.

- **Overleving** [berekend]: 1.956 HP, defense 0,949 plus second defense 0,375, ontwijken 80%. S = D212. Muurhoek b2 D153. Blok houdt tot D188. De sterkste overleving van alle acht.
- **Schade**: 79.882 per bitje, 798.821 DPS als alles raakt [berekend]. Het trefmodel geeft 100% tot 100 px [model]. Heks 0,5 s.
- **Lag** [model]: de zwaarste van alle acht. Score 1.370, de hele tijd, omdat de bitjes langer leven (gemiddeld 15 tegelijk in beeld).
- **Kosten**: 400 HC, 3.220 munten, 4 Ember-gebruiken.
- **Uit de save erbij (22):** Heirloom, ThirdEye, HeartGreed, CobraNecklace, Diary, SavageDictolydium, CowelRhys, LeofgarCasque, LeofgarPlate, HeavyIron, Stompers, Mandoletinas, LeoGreaves, IronMittens, 3x SnakeRune, 4x SeraLight, DogRune.
- **Let op:** loopsnelheid 40%: wegrennen gaat traag, dus blok of rol. Eigen pagina, geen upgrade van D1. Geen willekeurige embers.

---

## Eerlijke vergelijking

- **Snelst doden is D, niet C.** Op de cijfers doodt D een baas sneller dan C: met 2 melds D1 3,4 s tegen C1 5,1 s op D110 (D1 met het trefmodel), met 3 melds D2 0,3 s tegen C2 1,6 s [berekend]. C is de keuze als je zelf actief wilt spelen, een straal op afstand wilt en veel minder lag wilt dan D.
- **Lui en soepel gaan niet samen.** De luie builds maken de hele tijd objecten. Wil je echt weinig stotteren, dan is A de enige goede keuze.
- **A, C en D lijken van binnen op elkaar.** Ze delen een helm (CowelRhys) en een ontwijk-basis, dus ze overleven ongeveer even goed. Het verschil zit in hoe ze schade doen.
- **B1 leunt op de Melancholic.** Zonder die toevoeging aan je save haalt hij je overlevingswens niet.

## Wat ik van je nodig heb

1. **Welke builds** gaan naar pagina 6 tot en met 10? Mijn voorstel: nu A1, B1, C1 en D1 op 6 tot en met 9, en pagina 10 vrij houden. Na de Heks maak je B1 op dezelfde pagina tot B2, en kies je of A2, C2 of D2 op pagina 10 komt.
2. **Mag de Melancholic in je save?** Zonder is B1 te kwetsbaar (S D60); dan raad ik B af, of de zwakkere variant zonder riem.
3. **Mogen er onderdelen in je save worden toegevoegd** (17 tot 24 per build), of liever minder door onderdelen uit je pagina's 1 tot en met 5 te halen? Die pagina's veranderen dan.

Als je gekozen hebt, maak ik één lijst voor al je gekozen builds samen: welk stash-item op welke pagina komt en wat er in de save moet. Die lijst neem je mee naar Claude Code op je pc, die alles opnieuw controleert en de save schrijft met back-ups.

## Wat er na de controle is veranderd

Een aparte controleronde heeft alle acht builds nagelopen. Alle 96 slots zijn legaal bevonden. Deze punten zijn aangepast:

- De drankjes bij D genezen 90 HP, niet 180.
- A1 overleeft tot D143 en A2 tot D176, niet D153 en D230: het PestSlime-spuug is nu meegeteld.
- B1 zonder Melancholic (D60) staat er nu duidelijk bij.
- De knoppen kloppen nu met jouw instellingen (links is power).
- Meerdere muurklappen achter elkaar zijn bewezen. b2 is dus een echt risico, geen strenge ondergrens.
- De HC-som klopt nu: 300 + 300 + 400 + 400 = 1.400 van 1.423.
- D kreeg 2 ijsbitjes per beurt. Dat staat zo in de spelcode; de standaardsimulator telde er 1.
- Alle overlevingsgetallen zijn nu naar beneden afgerond.
- Het eigendom is opnieuw verdeeld: je pagina's 1 tot en met 5 en de Eclipse blijven standaard heel.

## Labels

- **[bewezen]**: staat zo in de spelcode of in de speldata. De bron staat in het technische deel hieronder.
- **[berekend]**: uitkomst van de simulator, die de rekenregels uit de spelcode naspeelt.
- **[afgeleid]**: mijn conclusie uit bewezen regels, niet apart doorgerekend.
- **[model]**: een schatting met aannames die niet uit de code komen, zoals het lag-model en het trefmodel van de ijsbitjes.
- **[onbewezen]**: niet uit de bestanden vast te stellen. Zie `OPEN_CODEVRAGEN.md`.

---

## Technical evidence (English)

### Method

- **Simulator.** `necro_sim.py` was rebuilt from the RULEBOOK and the disassembly. It reproduces 319 of 319 reference numbers from the previous session. An independent audit found 3 discrepancies against the bytecode and fixed them; its own checks then passed 140 of 140 and validate.py still passed 319 of 319:
  - the maxHealth clamp (f@2406);
  - `power_gain` reading pools C and D;
  - the burn execution term.
- **Search.** For each category, a designer searched every legal host+meld pair per slot (same CDB type, f@3643; Craftsman level 5 host types, f@6176; donor id ≠ host id, f@2737/f@2739; no Lyle items). Meld2 was then added on top of meld1 bases. Two verifiers per category (legality and category fit; numbers) checked each result, and the designers repaired every major finding.
- **Critic and reproduction.** A completeness critic re-ran all 8 builds through the stock simulator. I re-ran that script myself; the output was identical to the critic's. The corrections listed in the Dutch section were applied.
- **Rounding.** All D* values are floored.

### Survival model (stock simulator)

- **Mitigation.** M = damage_taken·(1−def)·(1−def·second_defense) (takeHit f@2428). Evade chance = e + (1−e)·se·e (attemptHit f@2426). Bounds: `bound` f@2774.
- **Enemy scaling.** Damage and HP scale by 1 + 0.03·D^1.65 (f@5947).
- **Scenarios a–g.** Popspore elite; Colossus hit + slam (n=1 and n=2); Crusher hit + slam; Goatman dash + slam; LastRemnant volley; PestSlime spew; barrage of 12 base damage at 3 hits/s for 600 s. S = min over a–f.
- **Wall slams.** touchWall f@2437 ops 16-43 uses lastHitDamage × knockback_damage, and takeHit overwrites lastHitDamage (op254). touchWall has no "already slammed" guard.
- **Walls.** Walls are merged rectangles (TileMap.generate f@5107/f@5110), and each new rectangle entered during one knockback calls touchWall again through onEnter (f@3479 ops 204-217). Chained slams are therefore real.
- **Block.** Poise-break thresholds come from the poise model in survival_report.

### Code facts verified in this round

- **Ice bits per emission: 2.**
  - ItemEffects.onUpdate f@2465 ops 227-258 calls createProjectiles('IceBit') with damage = calcDPS × ice_emission_damage and chainDepth = 1.
  - createProjectiles f@2622 ops 61-89: with chainDepth > 0, maxProj = max(3 − chainDepth, 1) = 2. If attack_count > 2, damage is multiplied by attack_count/2 and attack_count is set to 2.
  - getTargetList f@2621 ops 9-33 builds floor(attack_count) targets, and f@2622 ops 126-161 creates one projectile per target.
  - The stock `auto_damage` reports projectiles=2 but computes dps = per_projectile / 0.2, i.e. one projectile. The D figures in this document use per_projectile × 2 / 0.2.
  - At 60 FPS the emission timer gives 9.23 emissions/s (13 frames), per the D designer's reading of f@2465.
- **Heal per potion.** CDB HealthLarge health_gained has base 80 and increment 10, so q1 = 90. Heal = health_gained × potion_effect − health_lost (Equip.consume f@2753, addHealth f@2401). B has potion_effect 3.674, giving 331 HP.
- **Bindings.** settings.sav has bindings primary=[2] (middle) and primary_power=[0] (left); secondary keeps its default.
  - Holding the power key repeats: Player.hx:504-505 with isControlActive f@4035 and Input.postUpdate f@4043.
  - With an empty power bar the power key falls back to a normal attack: Equip.trigger f@2742 ops 143-161, Resources.hasPower f@3212.
- **Shaper path.** RULEBOOK §1.3 (River door f@5998 ops 54-70, 77 HC). The Witch has 2 HP bars and drops the ShapersKey: f@7847, f@7850, f@6434, f@7849, f@7851.
- **Final-door risk.** Refuge.enterLevel f@7521 op238 (flag), ops 239-244 (2.5 s timeout), op362 (save). FinalDoor f@6651 ops 97-111 and f@6657 op19.
- **Embers.** Items.dropItem f@3734 ops 99-107; ember_drop_rate ≤ 0 means no random ember drops.
- **Build Storage.** Swap Build f@10609 swaps 12 slots in the order of builds.json. The belt is not part of a page.

### Numbers that do not come from the stock simulator

- **B (burn spread).** The spread model, the trash-kill fractions and the Witch time come from the B designer's report script on top of the stock simulator. The stock burn tick (3,133.8 / 4,268.0) matches.
- **C (refill).** The refill-based figures assume the power bar stays full through executions (refill path f@2429 ops 224-256 -> f@2476 -> f@3210; not measured in game). The power-click period is (r_C + r_D)/2 per the C designer's reading of the code. For C1 r_C = r_D, so the figure equals the stock power DPS (41,427). For C2 the stock `power` figure (133,367) uses r_D alone; with the averaged period it is 130,819, which the critic reproduced.
- **D (hit rate).** H is a flight-and-hit model, not code. It assumes a stationary target, a fixed dt, no walls and no enemy evasion.
- **Lag.** All lag scores come from the lag model, whose weights are UNPROVEN; only the entity counts are proven.
- **Save additions.** Counts per build come from a greedy allocation over the clean stash objects in `ownership.json`. It excludes Build Storage pages 1-5 and all equipped items.

### Stock-simulator reproduction (per build)

| Build | maxHP | def / sdef | evasion | S (belt / no belt) | b2 | block < D | DPS (normal / power / mixed) | meld2 | HC | coins |
|---|---|---|---|---|---|---|---|---|---|---|
| A1 | 1025.6 | 0.944 / 0 | 0.859 | 143 / 143 | 89 | 114.1 | 34,793 / 6,129 / 34,146 | 0 | 0 | 3,580 |
| A2 | 1025.6 | 0.970 / 0 | 0.882 | 176 / 176 | 137 | 129.2 | 57,643 / 6,911 / 56,500 | 3 | 300 | 3,620 |
| B1 | 1160.0 | 0.947 / 0 | 0 | 152 / 60 | 96 / 30 | none | burn 15,669 per burner | 0 | 0 | 3,480 |
| B2 | 1376.0 | 0.961 / 0.375 | 0 | 206 / 111 | 167 / 61 | none | burn 21,340 per burner | 3 | 300 | 3,480 |
| C1 | 1088.0 | 0.938 / 0 | 0.815 | 141 / 141 | 84 | none | 5,035 / 41,427 / 9,409 | 0 | 0 | 3,180 |
| C2 | 1232.0 | 0.957 / 0 | 0.815 | 166 / 166 | 112 | 114.2 | 32,005 / 133,367 / 41,546 | 4 | 400 | 3,240 |
| D1 | 1476.8 | 0.930 / 0 | 0.801 | 150 / 150 | 83 | 92.6 | ice 11,008.6 per bit | 0 | 0 | 3,180 |
| D2 | 1956.8 | 0.949 / 0.375 | 0.801 | 212 / 212 | 153 | 188.8 | ice 79,882 per bit | 4 | 400 | 3,220 |
