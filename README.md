# Čo robí filmy obľúbenými/neobľúbenými
```
Projekt z predmetu Princípy dátovej vedy
Skupina: Lil Data
Členovia: Roderik Antol, Tomáš Belák, Adam Lopaška, František Václav Man
```

## Zdroj dát
Naše dáta pochádzajú z portálu IMDb - internetovej filmovej databázy. Stiahli sme si dáta vo formáte .tsv zo [stránky](https://datasets.imdbws.com/) a exportovali do databázy.

V práci používame primárne nami vytvorenú tabuľku `df_films`, ktorá vznikla spojením a dopočítaním viacerích tabuliek z našej databázy. V tabuľke máme nasledovné dáta o filmoch: 
- priemerné hodnotenie, 
- počet hodnotení, 
- nami vypočítané skóre (viac v nasledujúcej časti textu),
- počet prekladov filmu, 
- či je film pre dospelých, 
- rok výroby filmu, 
- dĺžka filmu v minútach, 
- žáner (jeden alebo viac) a 
- vek filmu - vypočítaný ako rok 2024 - rok výroby filmu.

Použité filtre na dáta:
- keďže chceme pracovať s filmami, odfiltrovali sme seriály, krátke filmy, videá a iné typy záznamov
- vybrali sme len hercov a režisérov a iba takích, ktorí pracovali na filmoch v našej tabuľke

Zároveň sme vyhľadali a pracovali aj s nasledujúcimi dátami
- 20 najlepších, najhorších hercov a režisérov sme spísali z štatistík na portáli IMDb
- Zoznam filmov, v ktorých hlavná postava mala nejaké znevýhodnenie (fyzické či psychické)

## Miera obľúbenosti
Pre definíciu miery obľúbenosti sme skúšali tri metriky. Prvou, a najlepšou bolo logskóre, vypočítané ako priemerné skúre filmu prenásobené logaritmom počtu hodnotení. 

Druhé skôre, ktoré sme skúšali, bolo normalizované skóre. Počítané ako priemerné skóre krát počet hodnotení filmu vydelené maximálnym skóre a maximálnym počtom hodnotení.

Ako tretie sme použili pragmatické skóre, počítané rovnako ako normalizované, iba namiesto maxím použijeme priemery. 

Z nasledujúcej tabuľky môžeme vidieť, že aj normalizované aj pragmatické skóre majú výraznejšie rozdiely medzi tretím a štrvtým kvartilom ako má log skóre. Log skóre bolo výhodnejšie aj z hľadiska matematických operácií a čitateľnosti, kde normalizované aj pragmatické skóre majú veľmi dlhé desatinné čísla. 

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

**TODO Prečo sme zvolili log skóre?**

**TODO Popísať nevýhodu log skóre -** `10 * log(10) = 1 * log(10^10)`, tj film s malo dobrymi hlasmi moze mat rovnake skore ako zly film s vela hlasmi

## Exploratívna dátová analýza
### Základné vlastnosti našich dát:

**TODO Rozdelenie log skóre**

![Histogram rozdelenia log skóre](./images/log_score_dist.png)

![Rozdelenie kategórií](./images/dist_of_categories.png)

Ako prvé sme pozreli, či a ako vplýva žáner filmu na jeho obľúbenosť. Z nasledujúcich grafov vidno, že skóre, resp. obľúbenosť, nemá významnú závislosť od žánru a skupín žánrov. Stredná hodnota korelácie je 4.3%, s tretím kvartilom na 6.8% percentách, čo je pod hranicou významnosti. Dva žánre, ktoré mali koreláciu nad 10%: Drama a Crime.

**TODO: Doplniť popis a vysvetlenia**

![Závislosť skóre od 1 žánru](./images/genres_score_corr.png)

Sumárne štatistiky pre koreláciu žánru od skóre.
|       |   log_score |
|:------|------------:|
| count |  27         |
| mean  |   0.0394699 |
| std   |   0.0512069 |
| min   |  -0.0727358 |
| 25%   |  -0.002215  |
| 50%   |   0.0432643 |
| 75%   |   0.0682588 |
| max   |   0.155022  |

![Závislosť skóre od viacerých žánrov](./images/genres2_score_corr.png)



TODO Heatmapy, korelačne grafy?

## Hypotézy a pozorovania
TODO
