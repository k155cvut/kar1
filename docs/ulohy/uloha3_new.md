---
icon: material/numeric-3-box
title: Úloha 3
---

# Srovnání kartografických zobrazení

Pro zadanou zemi vytvořte mapový výstup, který bude stát zobrazovat v několika kartografických zobrazeních a bude porovnávat plošné zkreslení těchto zobrazení. Kromě přednastavených kartografických zobrazení navrhněte také tři, která budou idealizovaná přímo pro vaše území.

## Postup v ArcGIS Pro:

- Vytvoříme nový projekt a nahrajeme [databázi zemí](https://github.com/jankoudy/KAR1/blob/main/uloha3/world_boundaries.zip) (_add data_)
- Z databáze zemí ponecháme pouze své zadání (_Definition Query_), citlivě odstraníme odlehlé ostrovy, změníme symbologii.
- Vypneme podkladové mapy.
- Budeme vytvářet celkem devět map, základní mapu v Mercatorově zobrazení si tak můžeme devětkrát nakopírovat. Pojmenovávat budeme mapy dle názvu zobrazení.
- Použijeme tato kartografická zobrazení:
    1. Mercatorovo zobrazení.
    2. 5 kartografických zobrazení dle vlastního výběru (Bonne, Winkel–Tripel, Cube, Mollweide, Spilhaus World Ocean, Robinson, Fuller, Plate Carée) – nastavujeme v _Map_ -> _Properties_ -> _Coordinate systems_ -> _Projected_ -> _World_.
    3. 3 kartografická zobrazení vhodná pro naše území (bude probráno později).
- Pro každé zobrazení nás zajímá, jak moc je v něm naše země plošně změněna. Cílem je tedy vypočítat plochu daného státu v daném kartografickém zobrazení. (nepůjde pro Mercatorovo zobrazení)
    1. Vrstvu obsahující náš polygon musíme nejprve předefinovat na správné zobrazení (_Analyses_ -> _Tools_ -> _Project_ -> nastavíme aktuální souřadnicový systém – _Current Map_).
    2. Nad nově vzniklou vrstvou (ve správných rovinných souřadnicích) vypočteme její obsah (můžeme využít sloupec rozloha -> _Calculate Geometry_).
- Pokud máme hotových všech devět dílčích map, můžeme vytvořit Layout (_Insert_ -> _New Layout_ -> _A3 Portraite_).
- Layout bude obsahovat všechny náležitosti mapy kromě legendy – název, mapová okna, měřítko, tiráž – vytvoříme společně během cvičení.

## Nalezení optimálních zobrazení:

Válcové zobrazení – cílem je získat ekvivalentní válcové kartografické zobrazení. Cest je několik, my využijeme myšlenku, že by bylo vhodné, aby nejsevernější bod území byl stejně délkově zkreslen jako ten nejjižnější. Respektive, aby tyto dva body dosahovaly délkového zkreslení stejně odlehlého od 1. U válcových zobrazení v normální poloze závisí délkové zkreslení v rovnoběžce pouze na zeměpisné šířce.

- Základní vzorce pro válcové zobrazení [ZDE](https://github.com/jankoudy/KAR1/blob/main/uloha3/vzorce.png).
- Sečtením ms a mj a následným dosazením a úpravou získáme vztah pro výpočet hodnoty nezkreslené rovnoběžky.
- Před výpočtem musím nalézt krajní body našeho území (nejjednodušší asi pomocí Calculate Geometry nad nějakým nepoužívaným sloupcem – minimum/maximum y-coordinate).
- V ArcGIS Pro existuje pro ekvivalentní válcové zobrazení název Cylindrical Equal Area, do parametrů vložím právě zjištěnou nezkreslenou rovnoběžku.

Azimutální zobrazení – i zde se pracuje s délkovým zkreslením na okraji našeho zájmového území. Azimutální zobrazení v obecné poloze nabízí stejné hodnoty zkreslení při stejné vzdálenosti od centra promítání. Cíl je tedy sevřít území v požadovaném zobrazení do opsané kružnice a zjistit souřadnice jejího středu. Naším požadovaným zobrazením bude Lambertovo ekvivalentní azimutální zobrazení.

- Postup hledání středu promítání je v této úloze iterační. Nejprve vytvoříme kružnici opsanou našemu území v Mercatorově zobrazení (_Tools_ -> _Minimum Bounding Geometry_ -> _Circle_) a zjistíme souřadnice jejího středu (_Calculate Geometry_ -> _Centriod x/y-coordinate_).
- Poté již nastavíme kartografické zobrazení na naše požadované (Lambert Azimuthal Equal Area), jako projekční centrum vyplníme zjištěné hodnoty v bodě výše.
- Proces provedeme znovu – vytvoříme kružnici opsanou, zjistíme její střed a pomocí těchto hodnot nastavíme znovu Lambertovo azimutální zobrazení. Toto zobrazení s těmito zjištěnými hodnotami již můžeme považovat za vhodné pro naše území.

Kuželové zobrazení – u kuželových zobrazení je výpočet ideálních hodnot nezkreslených rovnoběžek náročný, vychází ovšem z podobných požadavků, jako jsme probrali u válcových zobrazení. V případě zájmu se více můžete dočíst [ZDE](https://rozvoj.fsv.cvut.cz/zobrazeni/PLNY_TEXT.pdf). Pro naši úlohu využijeme nástroj pro volbu vhodného zobrazení přímo v softwaru ArcGIS Pro.

- Kromě nejsevernějšího a nejjižnějšího bodu území (jejich šířka) si zjistíme ještě nejzápadnější a nejvýchodnější souřadnice (jejich délka).
- _Map_ -> _Properties_ -> _Coordinate Systems_ -> _New suggested projected coordinate system_ -> zadáme okrajové souřadnice a upřesníme požadavek na plochojevné zobrazení.
- Pokud by ArcGIS Pro nenabídl žádné kuželové (Conic) zobrazení, vyzkoušíme ještě online nástroj [Projection Wizard](https://projectionwizard.org/), který funguje podobně. Pokud by nám tento nástroj nabídl nějaké kuželové zobrazení, nastavíme ho v ArcGIS dle zobrazených parametrů.

## Odevzdání:

Technická zpráva bude obsahovat podrobný popis tvorby mapového výstupu včetně mezikroků, které byly součástí příprav. Dále bude obsahovat výpočet nezkreslené rovnoběžky pro válcové zobrazení a všechny potřebné parametry tří vhodných zobrazení zadané země. Součástí technické zprávy bude také tabulka porovnávající rozlohu státu v jednotlivých zobrazeních. V závěru zkuste popsat, k čemu se primárně využívají zbylá kartografická zobrazení, která byla zobrazena.

Přílohou úlohy bude mapový výstup ve formátu A3.

## Zdroje dat    
[:material-download: World Boundaries (OpenDataSoft) :material-layers:](../assets/world_boundaries.zip){ .md-button .md-button--primary .button_smaller }
    {: .button_array style="justify-content:flex-start;"}

## Konkrétní zadání:

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

