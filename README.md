# Čo robí filmy obľúbenými/neobľúbenými
```
Projekt z predmetu Princípy dátovej vedy
Skupina: Lil Data
Členovia: Roderik Antol, Tomáš Belák, Adam Lopaška, František Václav Man
```

## Zdroj dát
Naše dáta pochádzajú z portálu IMDb - internetovej filmovej databázy. Stiahli sme si dáta vo formáte .tsv, exportovali do databázy a z nej vybrali nasledovné stĺpce:

- Názov filmu, 
- rok vydania filmu,
- dĺžka filmu v minútach
- žánre filmu - film môže mať jeden alebo viac žánrov

a neskôr pridáme aj stĺpce ako herec a režisér. 


## Miera obľúbenosti
Pre definíciu miery obľúbenosti sme skúšali tri metriky. Prvou, a najlepšou bolo logskóre, vypočítané ako priemerné skúre filmu prenásobené logaritmom počtu hodnotení. 

Druhé skôre ktoré sme skúšali bolo normalizované skóre, počítané ako priemerné skóre krát počet hodnotení filmu vydelené maximálnym skóre a maximálnym počtom hodnotení.

Ako tretie sme použili pragmatické skóre, počítané rovnako ako normalizované, iba namiesto maxím použijeme priemery. 

Z nasledujúcej tabuľky, môžeme vidieť, že aj normalizované a pragmatické skóre majú veľkých 

|       |   averageRating |         numVotes |    log_score |       norm_score |       prag_score |
|:------|----------------:|-----------------:|-------------:|-----------------:|-----------------:|
| count |    301868       | 301868           | 301868       | 301868           | 301868           |
| mean  |         6.17553 |   3627.84        |     28.0239  |      0.000898479 |      1.13691     |
| std   |         1.37358 |  35841           |     14.5419  |      0.0100013   |     12.6554      |
| min   |         1       |      5           |      1.79176 |      2.11646e-07 |      0.000267811 |
| 25%   |         5.3     |     19           |     17.8913  |      4.13768e-06 |      0.00523571  |
| 50%   |         6.3     |     61           |     24.6097  |      1.31432e-05 |      0.0166311   |
| 75%   |         7.1     |    315           |     34.1694  |      6.21367e-05 |      0.0786261   |
| max   |        10       |      2.83492e+06 |    138.175   |      0.93        |   1176.8         |


TODO Heatmapy, korelačne grafy?

## Hypotézy a pozorovania
TODO