---
title: Projektuppgift 7
permalink: /projekti7/
hide: true
---

# Projektuppgift 7

Som material för uppgift 1 används databasen `bikes_2024.db` som innehåller uppgifter om stadscykelturer i Helsingfors och Esbo under år 2024.

I denna uppgift ska du göra ett program som skapar databasen `bikes_2023.db` för år 2023. Data som ska ingå i databasen finns i CSV‑format och har [publicerats av HRT](https://www.avoindata.fi/data/fi/dataset/helsingin-ja-espoon-kaupunkipyorilla-ajatut-matkat).

Ditt program ska läsa datan från CSV‑filerna och utföra SQL‑kommandon som lägger in datan i databasen på samma sätt som i databasen i uppgift 1.

Observera att i CSV‑filen är cykelturerna för en viss månad i omvänd tidsordning. I databasen ska cykelturerna vara ordnade i kronologisk ordning, med den tidigaste cykelturen först. Du kan göra detta genom att lägga in raderna från varje CSV‑fil i omvänd ordning i databasen.

## Testa databasen

Du kan testa med följande frågor att innehållet i den databas du skapat verkar korrekt:

```console
sqlite> SELECT COUNT(*) FROM Stations;
459
sqlite> SELECT COUNT(*) FROM Trips;
2544025
sqlite> SELECT * FROM Stations WHERE id = 100;
100|Teljäntie
sqlite> SELECT * FROM Trips WHERE id <= 10;
1|2023-04-01T05:52:34|2023-04-01T14:28:14|87|140|3487|1224
2|2023-04-01T06:02:04|2023-04-01T06:06:57|49|19|992|288
3|2023-04-01T06:02:42|2023-04-01T06:08:10|35|19|1155|323
4|2023-04-01T06:03:40|2023-04-01T06:04:50|404|404|6|65
5|2023-04-01T06:11:38|2023-04-01T06:14:11|46|118|694|152
6|2023-04-01T06:18:06|2023-04-01T06:37:08|237|364|2770|1138
7|2023-04-01T06:19:59|2023-04-01T06:21:42|258|258|222|102
8|2023-04-01T06:27:52|2023-04-01T06:52:08|73|66|6260|1452
9|2023-04-01T06:36:57|2023-04-01T06:48:30|30|19|2313|689
10|2023-04-01T06:45:14|2023-04-01T06:53:41|62|59|1517|503
sqlite> SELECT * FROM Trips WHERE id = 123456;
123456|2023-04-18T15:18:42|2023-04-18T15:22:02|573|575|596|196
```

## Inlämning

Rapporten ska innehålla din kod.
