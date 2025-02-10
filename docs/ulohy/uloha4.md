---
icon: material/numeric-4-box
title: Úloha 4
---

Je dán bod P svými zeměpisnými souřadnicemi φ , λ {\displaystyle \varphi ,\lambda } na elipsoidu WGS84. Vypočtěte pravoúhlé souřadnice jeho rovinného obrazu a uveďte hodnotu délkového zkreslení v systému JTSK. Použijte vlastní skript v Matlabu. Helmertova transformace mezi elipsoidy: [zde](http://maps.fsv.cvut.cz/~cajthaml/vyuka/kar1/elipsoid.pdf)

__Pomocí software PROJ.4 vypočtěte rovinné pravoúhlé souřadnice bodu P a hodnotu délkového zkreslení:__

- v systému JTSK
- v systému UTM (33. šestistupňový pás, počátek posunut od průsečíku základního poledníku a rovníku o 500 km západně)

__Použití PROJ.4:__

- ``` (cs2cs +proj=latlong +datum=WGS84 +to +proj=krovak +ellps=bessel +towgs84=570.8,85.7,462.8,4.998,1.587,5.261,3.56) ```
- ``` (proj +proj=utm +datum=WGS84 +zone=33) ```


__Pomocí software ArcGIS vypočtěte rovinné pravoúhlé souřadnice bodu P:__

- v systému JTSK (transformace S_JTSK_To_WGS_1984_1)
- v systému UTM (33. šestistupňový pás, počátek posunut od průsečíku základního poledníku a rovníku o 500 km západně)


__Pro kartografická zobrazení používejte příslušné geodetické datumy (elipsoidy). Parametry transformace mezi nimi:__

- Bessel2WGS: 570.8,85.7,462.8,4.998,1.587,5.261,3.56

__Požadovaná přesnost výsledků:__ (souřadnice na cm), (zkreslení na 6 desetinných míst). 

## Číselné zadání:
| Číslo | \( \varphi \) | \( \lambda \) |
|--------|-------------|-------------|
| 1      | 49°10'      | 15°10'      |
| 2      | 49°10'      | 15°20'      |
| 3      | 49°10'      | 15°30'      |
| 4      | 49°10'      | 15°40'      |
| 5      | 49°10'      | 15°50'      |
| 6      | 49°20'      | 15°10'      |
| 7      | 49°20'      | 15°20'      |
| 8      | 49°20'      | 15°30'      |
| 9      | 49°20'      | 15°40'      |
| 10     | 49°20'      | 15°50'      |
| 11     | 49°30'      | 15°10'      |
| 12     | 49°30'      | 15°20'      |
| 13     | 49°30'      | 15°30'      |
| 14     | 49°30'      | 15°40'      |
| 15     | 49°30'      | 15°50'      |
| 16     | 49°40'      | 15°10'      |
| 17     | 49°40'      | 15°20'      |
| 18     | 49°40'      | 15°30'      |
| 19     | 49°40'      | 15°40'      |
| 20     | 49°40'      | 15°50'      |
| 21     | 49°50'      | 15°10'      |
| 22     | 49°50'      | 15°20'      |
| 23     | 49°50'      | 15°30'      |
| 24     | 49°50'      | 15°40'      |
| 25     | 49°50'      | 15°50'      |
| 26     | 50°00'      | 15°10'      |
| 27     | 50°00'      | 15°20'      |
| 28     | 50°00'      | 15°30'      |
| 29     | 50°00'      | 15°40'      |
| 30     | 50°00'      | 15°50'      |
| 31     | 51°10'      | 14°10'      |
| 32     | 51°10'      | 14°20'      |
| 33     | 51°10'      | 14°30'      |
| 34     | 51°10'      | 14°40'      |
| 35     | 51°10'      | 14°50'      |
| 36     | 51°20'      | 14°10'      |
| 37     | 51°20'      | 14°20'      |
