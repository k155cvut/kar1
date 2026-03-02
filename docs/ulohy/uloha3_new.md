---
icon: material/numeric-3-box
title: Úloha 3
---

Pro zadané státní území vzájemně porovnejte z hlediska hodnot délkového zkreslení:

- válcové konformní zobrazení o dvou nezkreslených rovnoběžkách (Mercatorovo)
- stereografickou azimutální projekci s nezkreslenou rovnoběžkou

Navrhujte obecnou polohu zvolených zobrazení. Nezkreslené rovnoběžky volte tak, aby vliv délkového zkreslení ve středu území a na okraji byl v absolutní hodnotě stejný.

Vyhotovte obrázky se zákresem státních hranic a zeměpisné sítě.

Rozhodněte, kolik bude zapotřebí souřadnicových soustav za podmínky, že vliv délkového zkreslení nepřekročí 20 cm/km.

V uvedených řešeních uvažujte referenční kouli. Výpočet zkreslení proveďte s přesností 6 desetinných míst, úhlové výpočty na minuty (na km v délce po povrchu Země).

[Shapefile se zeměpisnou sítí po 1°](http://maps.fsv.cvut.cz/~cajthaml/vyuka/kar1/latlong01.zip)

[Geodatabáze hranic států](http://maps.fsv.cvut.cz/~cajthaml/vyuka/kar1/svet.gdb.zip)

__Doporučený postup v ArcGIS Pro pro Mercatorovo zobrazení:__

1. otevřít GDB s hranicemi států, vybrat stát a exportovat do samostatného souboru
2. nastavit souřadnicový systém mapy v ArcGIS Pro na Mercator (world)
    1. Map - Properties - Coordinate Systems - Predefined - Projected - World - Mercator (world)
3. vytvořit minimální ohraničující obdélník s nejmenší šířkou
    1. Geoprocessing - Minimum Bounding Geometry
    2. nastavit vstup, výstup, RECTANGLE BY WIDTH
    3. nastavit okno aplikace, aby tam byl celý stát a v Environments nastavit u Output Coordinate System "Current Map", u Processing Extent "Current Display Extent"
    4. spustit funkci
4. získat souřadnice bodů uprostřed kratších stran (krajní body ortodromy, která prochází středem státu)
    1. vvytvořit novou bodovou vrstvu, nastavit Snapping na Midpoint, vytvořit 2 body
    2. v atributové tabulce přidat sloupce fi, lambda a vypočítat souřadnice ve WGS84 pomocí Calculate geometry nad sloupcem
5. nastavit souřadnicový systém mapy v ArcGIS Pro na Hotine (šikmé Mercatorovo zobrazení)
    1. Map - Coordinate Systems - New Projected Coordinate System - Hotine Oblique Mercator Two Point Center
    2. FE, FN nastavit na 0, doplnit zeměpisné souřadnice 2 dříve zjištěných bodů, Scale Factor nastavit 1, Latitude of Center 0
6. vytvořit minimální ohraničující obdélník s nejmenší šířkou (znovu, tentokrát již ve správnějším souřadnicovém systému)
    1. Geoprocessing - Minimum Bounding Geometry
    2. nastavit vstup, výstup, RECTANGLE BY WIDTH
    3. nastavit okno aplikace, aby tam byl celý stát a v Environments nastavit u Output Coordinate System "Current Map", u Processing Extent "Current Display Extent"
    4. spustit funkci
7. získat souřadnice bodů uprostřed kratších stran (krajní body ortodromy, která prochází středem státu) a v rohu
    1. vytvořit novou bodovou vrstvu, nastavit Snapping na Midpoint a Vertex, vytvořit 2 body uprostřed kratších stran a 2 v rozích
    2. v atributové tabulce přidat sloupce fi, lambda a vypočítat souřadnice ve WGS84 pomocí Calculate geometry nad sloupcem
8. odečíst souřadnice bodu na jedné z krajních rovnoběžek (roh obdélníku)
9. pomocí sférické trigonometrie vypočítat Š tohoto bodu
11. vypočítat délkové zkreslení na krajní rovnoběžce (závisí pouze na Š)
12. vypočítat kolik je potřeba souřadnicových soustav, aby zkreslení nepřesáhlo požadovanou hodnotu
13. vytvořit mapu
    1. přidat vrstvu s podkladem, např. World Topographic Base Map
    2. přidat vrstvu se zeměpisnou sítí s vhodným intervalem
    3. mapa bude obsahovat daný stát, obdélník a 3 body
    4. vložit Layout: Insert - New Layout - A4 (na šířku nebo délku)
    5. vložit Map Frame, nadpis, měřítko, tiráž

__Doporučený postup v ArcGIS Pro pro Stereografickou projekci:__

1. otevřít GDB s hranicemi států, vybrat stát a exportovat do samostatného souboru
2. nastavit souřadnicový systém mapy v ArcGIS Pro na Mercator (world)
    1. Map - Properties - Coordinate Systems - Predefined - Projected - World - Mercator (world)
3. vytvořit minimální ohraničující kružnici
    1. Geoprocessing - Minimum Bounding Geometry
    2. nastavit vstup, výstup, CIRCLE
    3. nastavit okno aplikace, aby tam byl celý stát a v Environments nastavit u Output Coordinate System "Current Map", u Processing Extent "Current Display Extent"
    4. spustit funkci
4. získat souřadnice středu kružnice
    1. Geoprocessing - Feature To Point
    2. v atributové tabulce přidat sloupce fi, lambda a vypočítat souřadnice ve WGS84 pomocí Calculate geometry nad sloupcem
5. nastavit souřadnicový systém mapy v ArcGIS Pro na Stereographic (stereografická projekce)
    1. Map - Coordinate Systems - New Projected Coordinate System - Stereographic
    2. FE, FN nastavit na 0, doplnit zeměpisné souřadnice středu, Scale Factor nastavit 1
6. vytvořit minimální ohraničující kružnici (znovu, tentokrát již ve správnějším souřadnicovém systému)
    1. Geoprocessing - Minimum Bounding Geometry
    2. nastavit vstup, výstup, CIRCLE
    3. nastavit okno aplikace, aby tam byl celý stát a v Environments nastavit u Output Coordinate System "Current Map", u Processing Extent "Current Display Extent"
    4. spustit funkci
7. získat souřadnice středu kružnice
    1. Geoprocessing - Feature To Point
    2. v atributové tabulce přidat sloupce fi, lambda a vypočítat souřadnice ve WGS84 pomocí Calculate geometry nad sloupcem
8. nastavit souřadnicový systém mapy v ArcGIS Pro na Stereographic (stereografická projekce)
    1. Map - Coordinate Systems - New Projected Coordinate System - Stereographic
    2. FE, FN nastavit na 0, doplnit zeměpisné souřadnice středu, Scale Factor nastavit 1
9. odečíst souřadnice libovolného bodu na kružnici
10. pomocí sférické trigonometrie vypočítat Š tohoto bodu
11. vypočítat délkové zkreslení na krajní kartografické rovnoběžce (závisí pouze na Š)
12. vypočítat poloměr kružnice, která má přesně požadované zkreslení
13. vytvořit mapu
    1. přidat vrstvu s podkladem, např. World Topographic Base Map
    2. přidat vrstvu se zeměpisnou sítí s vhodným intervalem
    3. mapa bude obsahovat daný stát, kružnici, střed a bod, dále požadované menší kružnice s maximálním povoleným zkreslením
    4. vložit Layout: Insert - New Layout - A4 (na šířku nebo délku)
    5. vložit Map Frame, nadpis, měřítko, tiráž


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

