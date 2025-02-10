---
icon: material/numeric-1-box
title: Úloha 1
---
# Výpočet zeměpisných souřadnic mezilehlých bodů loxodromy a ortodromy

Vypočítejte zeměpisné souřadnice mezilehlých bodů loxodromy a ortodromy dané koncovými body \( P_1(U_1, V_1) \) a \( P_2(U_2, V_2) \) na referenční kouli.  
Jako interval mezilehlých bodů použijte \( 5^\circ \) zeměpisné délky.

Proveďte zákres obou křivek v následujících kartografických zobrazeních. Jako podklad použijte síť poledníků a rovnoběžek vygenerovanou skriptem v prostředí MATLAB ([ukázka](http://maps.fsv.cvut.cz/~cajthaml/vyuka/kar1/u1/ukazka.m)).

### Válcové konformní zobrazení s jednou nezkreslenou rovnoběžkou (Mercatorovo)

\[
x = R \cdot V
\]

\[
y = R \cdot \ln \left( \tan \left( \frac{U}{2} + 45^\circ \right) \right)
\]

### Azimutální gnómonická projekce

\[
x = R \cdot \tan(90^\circ - U) \cdot \cos(V)
\]

\[
y = R \cdot \tan(90^\circ - U) \cdot \sin(V)
\]

### Lambertovo ekvivalentní válcové zobrazení

\[
x = R \cdot V
\]

\[
y = R \cdot \sin(U)
\]

### Mercator-Sansonovo nepravé válcové sinusoidální zobrazení

\[
x = R \cdot V \cdot \cos(U)
\]

\[
y = R \cdot U
\]


Dále vypočtěte délky obou křivek. Výpočty provádějte na referenční kouli s poloměrem \( R = 6380 \) km s přesností na úhlové vteřiny a mm.

## Číselné zadání

| číslo | U~1~ | V~1~ | U~2~ | V~2~ |
|-------|---------|---------|---------|---------|
| 1     | 5       | 10      | 50      | 80      |
| 2     | 5       | 10      | 50      | 90      |
| 3     | 5       | 10      | 50      | 100     |
| 4     | 5       | 10      | 50      | 110     |
| 5     | 5       | 10      | 50      | 120     |
| 6     | 5       | 10      | 50      | 130     |
| 7     | 5       | 10      | 60      | 80      |
| 8     | 5       | 10      | 60      | 90      |
| 9     | 5       | 10      | 60      | 100     |
| 10    | 5       | 10      | 60      | 110     |
| 11    | 5       | 10      | 60      | 120     |
| 12    | 5       | 10      | 60      | 130     |
| 13    | 5       | 10      | 60      | 140     |
| 14    | 5       | 10      | 70      | 80      |
| 15    | 5       | 10      | 70      | 90      |
| 16    | 5       | 10      | 70      | 100     |
| 17    | 5       | 10      | 70      | 110     |
| 18    | 5       | 10      | 70      | 120     |
| 19    | 5       | 10      | 70      | 130     |
| 20    | 5       | 10      | 70      | 140     |
| 21    | 5       | 20      | 50      | 80      |
| 22    | 5       | 20      | 50      | 90      |
| 23    | 5       | 20      | 50      | 100     |
| 24    | 5       | 20      | 50      | 110     |
| 25    | 5       | 20      | 50      | 120     |
| 26    | 5       | 20      | 50      | 130     |
| 27    | 5       | 20      | 60      | 80      |
| 28    | 5       | 20      | 60      | 90      |
| 29    | 5       | 20      | 60      | 100     |
| 30    | 5       | 20      | 60      | 110     |
| 31    | 5       | 20      | 60      | 120     |
| 32    | 5       | 20      | 60      | 130     |
| 33    | 5       | 20      | 60      | 140     |
| 34    | 5       | 20      | 70      | 80      |
| 35    | 5       | 20      | 70      | 90      |
| 36    | 5       | 20      | 70      | 100     |
| 37    | 5       | 20      | 70      | 110     |
| 38    | 5       | 20      | 70      | 120     |
| 39    | 5       | 20      | 70      | 130     |
| 40    | 5       | 20      | 70      | 140     |
