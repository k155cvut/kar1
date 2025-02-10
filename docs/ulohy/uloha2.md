---
icon: material/numeric-2-box
title: Úloha 2
---

# Zobrazení koule do roviny mapy

Je dáno zobrazení koule o poloměru \( R = 6380 \) km do roviny mapy zobrazovacími rovnicemi:

\[
x = R \cdot cotg U \cdot \sin(V \cdot \sin U)
\]

\[
y = R \cdot \left( cotg U \cdot (1 - \cos(V \cdot \sin U)) + U \right)
\]

Určete souřadnice obrazu daného bodu geografické sítě. Zjistěte vlastnosti daného zobrazení. V daném bodě vypočtěte veškeré charakteristické hodnoty:

- délkové zkreslení v poledníku \( m_p \),
- délkové zkreslení v rovnoběžce \( m_r \),
- úhel mezi obrazem poledníku a rovnoběžky \( \vartheta \),
- azimuty extrémního délkového zkreslení v originále \( A_{\varepsilon 1} \), \( A_{\varepsilon 2} \),
- azimuty extrémního délkového zkreslení v obraze \( A_{\varepsilon 1}^{'} \), \( A_{\varepsilon 2}^{'} \),
- hodnoty extrémních délkových zkreslení (poloosy Tissotovy indikatrix) \( a \), \( b \),
- maximální úhlové zkreslení \( \Delta \omega \),
- plošné zkreslení \( P \).


Vypočtené hodnoty zakreslete do Tissotovy indikatrix, která bude zobrazena ve vhodném měřítku nad geografickou sítí celého světa v daném zobrazení (interval 10 stupňů). Požadovaná přesnost výpočtu je u měřítek 6 desetinných míst, a pro úhly 1 úhlová vteřina. Číselné výsledky porovnejte s výsledky určenými v programu [**PROJ.4**](http://maps.fsv.cvut.cz/~cajthaml/vyuka/kar1/proj.zip) ([parametry](https://proj.org/usage/projections.html)).

## Číselné zadání

| číslo | \( U \) | \( V \) |
|-------|-------|-------|
| 1     | 10    | 70    |
| 2     | 10    | 80    |
| 3     | 10    | 90    |
| 4     | 10    | 100   |
| 5     | 10    | 110   |
| 6     | 10    | 120   |
| 7     | 10    | 130   |
| 8     | 10    | 140   |
| 9     | 10    | 150   |
| 10    | 10    | 160   |
| 11    | 20    | 70    |
| 12    | 20    | 80    |
| 13    | 20    | 90    |
| 14    | 20    | 100   |
| 15    | 20    | 110   |
| 16    | 20    | 120   |
| 17    | 20    | 130   |
| 18    | 20    | 140   |
| 19    | 20    | 150   |
| 20    | 20    | 160   |
| 21    | 60    | 70    |
| 22    | 60    | 80    |
| 23    | 60    | 90    |
| 24    | 60    | 100   |
| 25    | 60    | 110   |
| 26    | 60    | 120   |
| 27    | 60    | 130   |
| 28    | 60    | 140   |
| 29    | 60    | 150   |
| 30    | 60    | 160   |
| 31    | 70    | 70    |
| 32    | 70    | 80    |
| 33    | 70    | 90    |
| 34    | 70    | 100   |
| 35    | 70    | 110   |
| 36    | 70    | 120   |
| 37    | 70    | 130   |
| 38    | 70    | 140   |
| 39    | 70    | 150   |
| 40    | 70    | 160   |
