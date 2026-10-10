# Open codevragen

Stand: 10 oktober 2026. Game build 20114049.

Op 9 oktober stonden hier 20 vragen. Toen was alleen het verslag van de vorige sessie beschikbaar. Nu zijn ook `hlboot.dat` en de vertaalde spelcode (`alldis.txt`) gebruikt, en daarmee zijn de meeste vragen beantwoord. Wat overblijft, kan alleen een test in het spel of de geschiedenis van je save beantwoorden.

## Beantwoord

| # | Vraag | Antwoord | Bron |
|---|---|---|---|
| 1 | Is elke muurtegel een apart object? | Nee. Muren zijn samengevoegde rechthoeken. Elke nieuwe rechthoek die je tijdens één terugslag raakt, geeft wel een nieuwe muurklap, en die wordt steeds zwaarder. Hoeken en naden zijn dus gevaarlijk. [bewezen] | f@3781, f@5107/f@5110, f@3479 ops 204-217, f@2437 ops 16-43 |
| 2 | Kaatst de speler terug of glijdt hij? | Hij glijdt; het materiaal heeft elasticiteit 0. [bewezen] | f@3128, f@2926 |
| 3 | Flikkert stilstaan tegen een muur? | Nee. [bewezen] | f@4996 |
| 4 | Vertraagt bevriezing ook vijanden? | Alleen hun loopsnelheid, niet hun aanvalssnelheid. [bewezen] | f@5951 ops 64-115 |
| 5 | Kan melee vliegende bazen raken? | Ja. De vliegcontrole is code die nooit wordt uitgevoerd. [bewezen] | f@3478 ops 239-288 |
| 6 | Tellen Ronan en co als baas? | Alle 12 bazen zijn type Boss. Shatter, Foetus en enemy_start_health werken niet op bazen; instant_kill_threshold wel, behalve op Anguished. [bewezen] | CDB, f@2466, f@6813, f@5913, f@5951 ops 342-404 |
| 7 | Hoe lang blijven gevarenprojectielen liggen? | AdriftFire 4 s, FireTrail 0,5 s, StaticSpark 1 s (daarna een bliksem), Wickedfire 1,5 s. Schade alleen bij binnenkomen. [bewezen] | f@2642 ops 496-622, f@2616, f@7995 |
| 8 | Loopt het spel vast na LastRemnant? | Nee. Zijn ClearLevel loopt nooit, maar de deur en de beloning werken. [bewezen] | f@6369, f@7605 |
| 9 | Wat doet "Continue" na stoppen midden in een run? | Het niveau wordt opnieuw opgebouwd met dezelfde seed en de stand van bij binnenkomst. De run is niet mislukt; alleen de voortgang in dat niveau is weg. [bewezen] | f@5709, f@5710, f@3961 tot f@3460, f@3469 |
| 10 | Wekt RunePhoenix je tot leven? | Nee; de uitkomst van die controle wordt nooit gebruikt. Wapen en offhand loslaten bij doodgaan doet niets. [bewezen] | f@3864 ops 5-13, f@2744/f@2745 |
| 11 | Is de Heks te verslaan? Kunnen Lyle-items vallen? | Ja, ze heeft 2 HP-balken. Lyle-items kunnen zelden vallen, alleen boven moeilijkheid 50. Er is wel een vastloop-risico bij de laatste deur; zie RESULTAAT.md. [bewezen] | f@7847, f@7850, f@6434, f@7849, f@7851, f@3743, f@7521, f@6651, f@6657 |
| 12 | Waar komt watcher level 10 vandaan? | Te verdienen in het spel: maximaal level 10, elk level +10 max HP. Of jij het verdiend hebt, staat hieronder bij de open vragen. [bewezen] | f@6750-f@6752, f@3857 |
| 13 | Welk type krijgen de slots van een Build Storage-pagina? | Vastgesteld uit de constructor. [bewezen] | f@3733 |
| 15 | Op welke videokaart draait het spel? | Nog open, zie hieronder. | |
| 16 | Welk item is host en welk meld? | Vervallen. De nieuwe builds noemen host en meld apart. Mandoletinas is altijd de meld, omdat hij als host de defense op een vaste waarde zet. | f@2732 ops 82-103 |
| 17 | Wat haalt de build zonder Melancholic? | Doorgerekend: B1 zonder Melancholic overleeft tot D60. | RESULTAAT.md |
| 18 | DPS van VanceDagger met Heirloom? | Doorgerekend voor A1: 34.793 DPS met de gewone steek. | RESULTAAT.md |
| 19 | Welke items heb je al schoon? | Vastgesteld uit je save; per build verwerkt in "Uit de save erbij". | eigendomslijst uit de save |
| 20 | Welke build haalt de hoogste Wotana-trede? | Vervallen. Elke build heeft nu zijn eigen overlevingsgrens per dreiging. | RESULTAAT.md |

Vraag 14 (schrijft de serializer velden altijd alfabetisch?) is half beantwoord; het open deel staat hieronder.

## Nog open

### Testen in het spel

1. **Videokaart en fps.** Draait het spel op de RTX 4070 als je in Windows voor Necrovale.exe "Hoge prestaties" kiest? Hoeveel fps haal je met A1 en met D1? Het lag-model is een schatting en de gewichten zijn niet gemeten.
2. **Trefkans van de ijsbitjes (D1, D2).** Het trefmodel gaat uit van stilstaande vijanden en geen muren. Bewegende projectielen verdwijnen tegen muren (f@2492 ops 80-84), dus naast een muur raken minder bitjes [afgeleid]. Hoeveel minder, is niet doorgerekend.
3. **Brandtikken bij lage fps (B1, B2).** Is er een limiet op het aantal tikken per frame? En hoeveel rekenwerk kost het opzoeken van buren als honderden vijanden branden?
4. **Melancholic in riemvak 1 (B1, B2).** Blijft hij staan na doodgaan en na een levelwissel? Uit de code afgeleid: ja, want alleen drinken of zelf verslepen haalt hem weg. Niet in het spel getest.
5. **Krachtbalk aan het begin van een level (C1, C2).** Is hij leeg? Afgeleid: gewone klappen met executies vullen hem binnen een paar klikken.
6. **"Executed"-teksten en het BloodBeam-spoor (C1, C2).** Hoeveel frames kosten die? Niet doorgerekend.
7. **Raakvlak van de dolksteek (A1, A2).** Bereik en hoek zijn berekend, het oppervlak is niet bemonsterd.

### Geschiedenis van je save

8. **Zijn je 1.500 HC, watcher level 10 en de losse stash-items in het spel verdiend?** Uit één save valt dat niet af te lezen. Wel bewezen: de 43 objecten met een ongeldige derde meld (pagina 3, 4 en 5 en de Eclipse) zijn precies wat het oude script `write_builds.py` heeft geschreven.
9. **Wat betekent de vlag `door_fear_41`?** Die staat aan, terwijl het Seal of Fear nog niet gebroken is.

### Alleen voor het schrijven van de save

10. **Volgorde van velden (vraag 14).** De volgorde van de serializer is deels vastgesteld (f@9494). De volgorde van de ingebouwde `Reflect.fields` niet. Het spel laadt velden op naam, dus dit raakt alleen de grootte van het verschil in het save-bestand.

### Niet onderzocht

CursedFlask-ritme, de volgorde in Attack.preUpdate, HornslackGuard, de explosie van een HandCannon als meld, de volgorde waarin deuren worden verzameld, een crash bij een voorbeeld zonder eigenaar en de timing van de power-modus.
