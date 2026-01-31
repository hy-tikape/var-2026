---
title: Projektuppgift 1
permalink: /projekti1/
hide: true
---

# Projektuppgift 1

Datan i denna uppgift utgörs av en databas som innehåller uppgifter om cykelturer som gjorts med stadscyklarna år 2024 i Helsingfors och Esbo. Databasen bygger på data som [publicerats av HSL](https://www.avoindata.fi/data/fi/dataset/helsingin-ja-espoon-kaupunkipyorilla-ajatut-matkat) och som har omvandlats till en SQLite-databas för användning i denna kurs.

Du kan ladda ner databasen här: [bikes_2024.zip](https://cs.helsinki.fi/u/ahslaaks/bikes_2024.zip)

Databasen innehåller följande två tabeller:

```sql
CREATE TABLE Stations (
    id INTEGER PRIMARY KEY,
    name TEXT
);

CREATE TABLE Trips (
    id INTEGER PRIMARY KEY,
    start_time TEXT,
    end_time TEXT,
    start_station_id INTEGER REFERENCES Stations,
    end_station_id INTEGER REFERENCES Stations,
    distance INTEGER,
    duration INTEGER
);
```

I kursmaterialet finns mer detaljerad information om databasens innehåll och exempel på databassökningar.

Din uppgift är att skriva kod som innehåller följande funktioner som använder databasen. Du kan själv bestämma i vilken form funktionerna exakt ger resultaten. Det viktiga är att du med hjälp av funktionerna kan hämta de exempelresultat som nämns i deluppgifterna.

Du får ett visst antal poäng för varje deluppgift. Din poäng för uppgiften är summan av poängen för de deluppgifter du har löst.

## Deluppgift 1 (4 poäng)

* Skapa funktionen `trips_from_station(station_name)` som returnerar antalet cykelturer som startat från den angivna stationen.
* Skapa funktionen `trips_to_station(station_name)` som returnerar antalet cykelturer som avslutats vid den angivna stationen.

Funktionerna ska ge som resultat exempelvis att 8535 resor har startat från stationen 'Intiankatu' och att 8448 resor har avslutats vid den stationen.

## Deluppgift 2 (5 poäng)

* Skapa funktionen `longest_distance_trips(limit)` som returnerar de `limit` längsta cykelturernas längd samt deras respektive start- och slutstationer.
* Skapa funktionen `longest_duration_trips(limit)` som returnerar de `limit` cykelturer som varade längst samt deras respektive start- och slutstationer.

Funktionerna ska ge följande resultat när `limit` är 5:

| Startstation         | Slutstation          | Avstånd (m) |
|--------------------|----------------------|-------------------|
| Erottajan aukio    | Unioninkatu          | 655225            |
| Gunillantie        | Workshop Helsinki    | 425905            |
| Pajamäki           | Paloheinän kirjasto  | 393434            |
| Tupasaarentie      | Marjaniementie       | 277991            |
| Pitäjänmäen asema  | Workshop Helsinki    | 262121            |

| Startstation       | Slutstation      | Varaktighet (s) |
|------------------|------------------|-------------------|
| Lintulahdenkatu  | Marjaniementie   | 6286982           |
| Tupasaarentie    | Marjaniementie   | 4649106           |
| Ehrenströmintie  | Workshop Helsinki| 4396006           |
| Matinkyläntie    | Paciuksenkaari   | 4000567           |
| Kuikkarinne      | Trumpettikuja    | 3987658           |

Sidnot: Dessa uppgifter verkar inte trovärdiga eftersom den avståndsmässigt längsta cykelturen var 655 km och den cykeltur som varade längst tog 73 dagar.

## Deluppgift 3 (6 poäng)

* Skapa funktionen `trips_during_month(month)` som returnerar antalet cykelturer som startat under den angivna månaden. Här motsvarar 1 januari, 2 februari, och så vidare.
* Skapa funktionen `trips_during_weekday(day)` som returnerar antalet cykelturer som startat på den angivna veckodagen. Här motsvarar 1 måndag, 2 tisdag och så vidare.

Funktionerna ska ge följande resultat:

| Månad  | Antal resor |
|-----------|----------------:|
| April  | 167960          |
| Maj  | 448518          |
| Juni   | 469132          |
| Juli  | 455422          |
| Augusti    | 492348          |
| September   | 340507          |
| Oktober   | 211781          |

| Veckodag      | Antal resor |
|------------|----------------:|
| Måndag  | 379173          |
| Tisdag    | 423740          |
| Onsdag| 405657          |
| Torsdag    | 406417          |
| Fredag  | 367325          |
| Lördag   | 311952          |
| Söndag  | 291404          |

## Deluppgift 4 (7 poäng)

* Skapa funktionen `most_popular_start_stations(limit)` som returnerar de `limit` mest populära startstationerna.
* Skapa funktionen `least_popular_start_stations(limit)`, som returnerar de `limit` minst populära startstationerna.

Funktionerna ska ge följande resultat när `limit` är 5:

| Station                  | Antal avgångar |
|------------------------|----------------|
| Itämerentori           | 50441          |
| Töölönlahdenkatu       | 36382          |
| Rautatientori / länsi  | 32415          |
| Pasilan asema          | 30910          |
| Kalasatama (M)         | 28352          |

| Station                    | Antal avgångar |
|--------------------------|----------------|
| Relay Box test station   | 9              |
| Workshop Helsinki        | 26             |
| Puistolan VPK            | 393            |
| Sateenkaarentie          | 418            |
| Jakomäentie              | 481            |

Här verkar "Relay Box test station" vara en teststation och "Workshop Helsinki" ett cykelgarage. Den minst populära startstationen verkar således vara "Puistolan VPK".

## Deluppgift 5 (8 poäng)

* Skapa funktionen `largest_differences(limit)` som returnerar de `limit` största skillnaderna mellan antalet cykelturer som startat och antalet cykelturer som avslutats vid en station.

Funktionen ska ge följande resultat när `limit` är 5:

| Station                 | Antal startade resor| Antal avslutade resor | Skillnad |
|-------------------------|------:|--------:|--------:|
| Pasilan asema           | 30910 |   26670 |    4240 |
| Karhupuisto             |  9686 |    8018 |    1668 |
| Sompasaari              | 21604 |   23158 |    1554 |
| Vallilan varikko        |  6068 |    4647 |    1421 |
| Opastinsilta            |  5905 |    4550 |    1355 |

## Inlämning

Rapporten ska innehålla din kod.
