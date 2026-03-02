---
icon: material/numeric-2-box
title: Úloha 2
---

# Zobrazení Země na mnohostěnu

Vytvořte papírový 3D model Země na pravidelném dvanáctistěnu. Tuto aproximaci zemského povrchu proveďte v gnómonické projekci pomocí softwaru ArcGIS Pro. Pro hlavní město zadaného státu vypočtěte plošné zkreslení, maximální hodnotu úhlového zkreslení a extrémní hodnoty délkového zkreslení. Zadaný stát v modelu zvýrazněte. Vypočtěte také extrémní hodnoty těchto zkreslení pro vytvořenou aproximaci (okraje pětiúhelníků). Získané hodnoty porovnejte s výsledky z programu PROJ.

Více o aproximaci Země na mnohostěnu [ZDE](https://maps.fsv.cvut.cz/diplomky/2010_BP_Kozak_Zobrazeni_Zeme_na_pravidelnych_mnohostenech.pdf).

## Postup v ArcGIS Pro:

- Vytvoříme nový projekt, nahrajeme [databázi zemí](https://github.com/jankoudy/KAR1/blob/main/uloha2/world_boundaries.zip) (_add data_), [souřadnicovou síť](https://github.com/jankoudy/KAR1/blob/main/uloha2/lonlat.zip) a [tabulku s body](https://github.com/jankoudy/KAR1/blob/main/uloha2/body_2.csv).
- Z databáze zemí ponecháme pouze své zadání (_Definition Query_), citlivě odstraníme odlehlé ostrovy, změníme symbologii.
- Souřadnicovou síť zobrazíme pouze po deseti stupních (_Definition Query_) a změníme symbologii.
- Z tabulky bodů vytvoříme bodovou vrstvu (_add data_ -> _XY table to point_ -> X=délka, Y=šířka).
- Zvolíme vhodnou základní mapu.
- Nyní je potřeba vytvořit jednotlivé pětiúhelníky pro samotnou tvorbu 3D modelu, nahrané body jsou vrcholy těchto pětiúhelníků. Každý ale musíme zobrazit v konkrétním kartografickém zobrazení (gnómonická projekce s konkrétním středem promítání)
    1. Musíme tak vytvořit 12 map, každá bude v jiném zobrazení na základě středu promítání.
    2. Vytvoříme si 12 map v předem nastavené projekci, každou poté zobrazíme ve správném kartografickém zobrazení.
    3. _Map_ -> _Properties_ -> _Coordinate Systems_ -> _New Projected Coordinate System_ -> nastavíme Gnomonic a vyplníme správné souřadnice projekčního centra.
    4. Takto nastavené zobrazení zobrazíme v určitém měřítku (stačí nalézt nějaké, ve kterém uvidím všech pět bodů pětiúhelníku v mapovém okně. Stejné měřítko je dobré použít pro každý z pětiúhelníků).
    5. Jednoduše si vytvoříme printscreen tohoto pětiúhelníku a uložíme ho.

Souřadnice pro nastavování gnómonické projekce [ZDE](https://github.com/jankoudy/KAR1/blob/main/uloha2/body.png).

## Postup při vytváření modelu:

Vytvoření samotného 3D modelu je na každém individuálně. Existuje více možností na základě schopností práce s různými např. grafickými program.

Každý si také volí formát papíru, ve kterém síť pro slepení modelu vytiskne. Model z formátu A3 je zhruba 12 cm široký. Šel by tak poslepovat i na menším formátu, vytvořit lze ale i na větším formátu.

Jedna z jednoduchých možností: vytiskneme si přiloženou [šablonu](https://github.com/jankoudy/KAR1/blob/main/uloha2/skladacka_tisk.pdf) pro skládání dvanáctistěnu, změříme rozměry takto vytištěných pětiúhelníků, jednotlivé “mapy“ ořízneme dle nejširšího rozestupu bodů a vložíme do Wordu, nastavíme velikost obrázku dle změřené délky, vytiskneme ve správných rozměrech a nalepíme na předem vytištěnou síť, poté model složíme.

## Výpočet zkreslení:

Výpočet zkreslení provedeme dvojí, ruční a v softwaru PROJ.

Pro jednotlivé druhy distorze platí tyto [VZTAHY](https://github.com/jankoudy/KAR1/blob/main/uloha2/vzorce.png).

Program PROJ funguje pomocí příkazové řádky. Řádka, která vypočítá zkreslení bodu v gnómonické projekci může vypadat například takto:

echo 14.4 50.1 | proj -V +proj=gnom +lat_0=26.6 +lon_0=36 +R=6378000

- echo 14.4 50.1 -> zajímá nás pouze jeden konkrétní bod.
- proj -V +proj -> V nám zajistí podrobné informace o zkreslení i s popisem (S by vypsalo hodnoty bez popisu).
- gnom +lat_0=26.6 +lon_0=36 -> takto nadefinujeme gnómonickou projekci s konkrétním středem promítání.
- +R=6378000 -> definujeme, že výpočet probíhá na kouli, volba poloměru nemá na výpočet vliv.

Po úspěšném výpočtu dostanu několikařádkovou informaci o konkrétním bodě v konkrétním kartografickém zobrazení.

## Instalace PROJ:

Ze stránek [PROJ](https://proj.org/en/stable/install.html) stáhneme program dle návodu. Vyzkoušeno nedávno, mělo by vše fungovat. Dávat si pozor, kam je staženo. Nutno pak znát cestu k souborům pro práci v příkazové řádce.

Stáhne se rovnou i podpůrný program OSGeo4W, usnadní práci s příkazovou řádkou.

## Odevzdání:

Technická zpráva – popsat postup řešení úlohy a samotnou tvorbu modelu. Ve výpočetní části uvést potřebné vzorce a souřadnice, ze kterých výpočty vycházejí. Výsledné hodnoty porovnáme s výsledky ze softwaru PROJ.

3D model - donést fyzicky ke kontrole, pak bude vrácen.

## Číselné zadání

| Číslo  | Stát           |
|--------|----------------|
| 1	     | Mexiko         |
| 2	     | Argentina      |
| 3	     | Bolívie        |
| 4	     | Portugalsko    |
| 5	     | Japonsko       |
| 6	     | Mongolsko      |
| 7	     | Kazachstán     |
| 8	     | JAR            |
| 9	     | Namibie        |
| 10     | Madagaskar     |
| 11     | Mosambik       |
| 12     | Botswana       |
| 13     | Alžírsko       |
| 14     | Mauritánie     |
| 15     | Libye          |
| 16     | Egypt          |
| 17     | Saúdská Arábie |
| 18     | Írán           |
| 19     | Turecko        |
| 20     | Niger          |
| 21     | Čad            |
| 22     | Súdán          |
| 23     | Francie        |
| 24     | Německo        |
| 25     | Polsko         |
| 26     | Itálie         |
| 27     | Španělsko      |
| 28     | Rumunsko       |
| 29     | Island         | 
| 30     | Velká Británie |
| 31     | Indie          |
| 32     | Etiopie        |
| 33     | Finsko         |
| 34     | Švédsko        |
| 35     | Tanzanie       |
| 36     | Angola         |
| 37     | Paraguay       |
| 38     | Peru           |
| 39     | DR Kongo       |
| 40     | Pákistán       |
