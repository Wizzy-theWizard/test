# Open codevragen

Dingen die niet uit de beschikbare spelbestanden vast te stellen waren. De vorige sessie had geen `hlboot.dat`, alleen eerder uitgepakte codedumps (build 20114049). Alles wat een functie nodig had die niet gedumpt was, staat hier.

Per vraag: wat er onbekend is, waar het antwoord zou moeten zitten, en waarom het uitmaakt.

## Gevechtsregels

1. **Is elke muurtegel een apart object?**
   Bron: `eng.Orthomap.getBodiesFromIds` f@3781.
   Belang: als ja, geeft schuiven langs een muur een muurklap per tegel. Bewezen is alleen dat een hoek van muur plus deur of kist twee klappen geeft. Vanaf ongeveer D160 wordt elke volgende klap groter dan de vorige.

2. **Kaatst de speler terug of glijdt hij langs de muur?**
   Bron: `echo.Listener.get_defaults` en de elasticiteit van het echo-materiaal.
   Belang: zelfde als vraag 1.

3. **Flikkert een rustend contact tussen "enter" en "exit"?**
   Bron: echo SAT / `Collisions.query` f@4812.
   Belang: als ja, kan stilstaan tegen een muur herhaalde klappen geven.

4. **Raakt de bevriezing ook vijanden langzamer?**
   Bewezen is het alleen voor de speler (snelheid en aanvalssnelheid gedeeld door 1,5).
   Belang: bepaalt hoe veilig de kill-kern K1b is.

5. **Kan melee vliegende bazen raken (NowhereGuide, Mortopavida)?**
   Bron: `Physics.condition` f@3478, regels 150-152.
   Belang: bepaalt of een melee-build tegen 2 van de 10 Wotana-bazen kan winnen.

6. **Zijn Ronan, Roarke, MagnaBestia, BloodlessKing en LastRemnant van klasse Boss of Enemy?**
   Belang: shatter, Foetus en enemy_start_health werken niet op bazen. Als een van deze als Enemy telt, werken ze wel.

7. **Hoe lang blijven stilstaande gevarenprojectielen liggen?** (AdriftFire, FireTrail, StaticSpark, Wickedfire)
   Belang: lag en schade bij lange baasgevechten.

8. **Wordt de ClearLevel van LastRemnant ooit uitgevoerd?** Zijn `die` stuurt geen `enemy_killed`.
   Belang: mogelijke vastloper na die baas.

## Dood, opslaan en Wotana

9. **Wat doet "Continue" na stoppen midden in een run?**
   Bron: `World.deserialize` f@3460 (niet gedumpt).
   Belang: als het niveau opnieuw wordt opgebouwd, is stoppen een gratis herkansing zonder verlies. Nu alleen een noodgreep, geen plan.

10. **Wekt RunePhoenix je weer tot leven, en wat doet "release" met wapen en offhand bij doodgaan?**
    Bron: `Player.die` f@3864 ops 5-13; f@2422 en f@2424.
    Belang: kosten van een dood in Wotana.

11. **Is de Witch te verslaan zonder dat de laatste deur vastloopt? Kunnen Lyle-items vallen?**
    Bron: RULEBOOK §9 van het oude onderzoek.
    Belang: zonder Witch geen Wotana-sleutel en geen Shaper's Anvil. Set 1 en 2C hangen hiervan af.

## Save en inventaris

12. **Waar komen de 1500 hope crystals en `watcher_level` 10 (+100 maxHP) vandaan?**
    Belang: als de crystals toegevoegd zijn, is 2C formeel niet "eerlijk" verdiend.

13. **Welk `type` krijgen de 12 slots van een Build Storage-pagina?**
    Bron: `proc.Inventory`-constructor f@3733.
    Belang: alleen voor slepen in het menu. "Swap Build" werkt zonder deze check.

14. **Schrijft de serializer velden altijd alfabetisch?**
    Belang: alleen voor een zo klein mogelijk verschil in het save-bestand. Het spel laadt de velden op naam.

## Prestaties

15. **Op welke videokaart draait het spel nu, en werkt de prestatiemod?**
    Het spel opent op het 144 Hz-scherm van de AMD-iGPU. Er is geen GPU-voorkeur ingesteld voor Necrovale.exe. De mod uit de overdracht is gebouwd maar nooit gestart.
    Belang: waarschijnlijk de grootste winst voor set 3, maar onbewezen.

## Ontstaan bij het afronden (9 oktober)

16. **Welk item is host en welk is meld in de paren uit de defense/evasion-zoektocht?**
    De resultaten noteren paren als "A+B". Meestal staan ze alfabetisch, maar niet altijd ("Stompers+Mandoletinas"). Bewezen is dat Mandoletinas als host de defense op 0 zet, dus in "Mandoletinas+Winklepickers" (2B) moet Mandoletinas de meld zijn. In `builds.json` staat het eerste item als host, behalve bij Mandoletinas.
    Belang: bij paren waar host en meld verschillende Power-, SET- of aanvalsregels hebben, verandert de volgorde de cijfers. Narekenen met de simulator.

17. **Wat halen 2A, 2B en 3A zonder Melancholic in de gordel?**
    De zoektocht deed ook alle doelen zonder gordelpotion, maar die tabellen staan maar gedeeltelijk in het verslag.
    Belang: je hebt geen Melancholic. Zonder toevoeging aan de save zijn de cijfers van set 2 te optimistisch.

18. **Wat is de DPS van VanceDagger ← Heirloom met de uitrusting van 2A?**
    De gemeten 22.757 DPS hoort bij andere uitrusting.

19. **Welke items van set 2 en 3 heb je al schoon in bezit?**
    De volledige eigendomstabel van de vorige sessie is weg. `must_add_to_save` noemt alleen wat zeker is.

20. **Welke combinatie van kill-kern en verdediging haalt de hoogste Wotana-trede?** (set 1)
    Vereist de simulator en `data.cdb.json`.

Voor 16 tot en met 20 is geen nieuwe spelcode nodig, alleen de bestanden uit de zip en de simulator.
