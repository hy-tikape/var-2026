---
title: Projektuppgift 6
permalink: /projekti6/
hide: true
---

# Projektuppgift 6

MongoDB är en populär NoSQL‑databas som inte bygger på relationsmodellen och SQL‑språket som de flesta traditionella databaser. I denna uppgift ska du hämta information från en befintlig databas som innehåller uppgifter om bostäder och deras försäljningshistorik.

Din uppgift är att ta reda på hur man hämtar information från en MongoDB‑databas genom programmering. Kursmaterialet innehåller ingen information om detta, men du får använda nätkällor och artificiell intelligens som hjälp.

Databasen som hör till uppgiften finns på MongoDB Atlas molntjänst. Du får åtkomst till databasen i koden med följande användarnamn och lösenord:

* Användarnamn: `tikape`
* Lösenord: `NAq8a4pNLWF8TMfd`

Denna användare har läsrättigheter till databasen, vilket innebär att du kan läsa datan i databasen men inte ändra den. Uppgiften går ut på att hantera databasen genom att skapa ett program som ansluter till databasen med det ovan angivna användarnamnet och lösenordet.

## Anslutning till databasen (Python)

Följande Python‑kod ansluter till databasen och hämtar data därifrån:

```python
import pymongo

connection_string = "mongodb+srv://tikape:NAq8a4pNLWF8TMfd@cluster0.u4vehy9.mongodb.net/"
client = pymongo.MongoClient(connection_string)

database = client.get_database("tikape")
apartments = database["apartments"]

count = apartments.count_documents({})
print(count)

first_apartment = apartments.find_one()
print(first_apartment)
```

Kodens resultat ser ut på följande sätt:

```
1000
{'_id': ObjectId('679e1f6ef33fbe011e152685'), 'zip_code': '00780', 'apartment_size': 109, 'construction_year': 1996, 'transactions': [{'date': '2005-08-21', 'selling_price': 548582}, {'date': '2011-04-28', 'selling_price': 545161}, {'date': '2013-01-20', 'selling_price': 550660}, {'date': '2019-12-06', 'selling_price': 538431}, {'date': '2024-11-25', 'selling_price': 548912}]}
```

Observera att om du försöker köra koden själv kan den visa information om en annan bostad. Koden hämtar uppgifter om någon bostad som finns i databasen.

## Anslutning till databasen (R)

Följande R‑kod ansluter till databasen och hämtar data därifrån:

```r
connection_string <- "mongodb+srv://tikape:NAq8a4pNLWF8TMfd@cluster0.u4vehy9.mongodb.net/"

apartments <- mongo(collection = "apartments", db = "tikape", url = connection_string)

print(apartments$count())

print(apartments$find(limit = 1))
```

Kodens resultat ser ut på följande sätt:

```
[1] 1000

  zip_code apartment_size construction_year                                                                                       transactions
1    00780            109              1996 2005-08-21, 2011-04-28, 2013-01-20, 2019-12-06, 2024-11-25, 548582, 545161, 550660, 538431, 548912
```

Observera att om du försöker köra koden själv kan den visa information om en annan bostad. Koden hämtar uppgifter om någon bostad som finns i databasen.

## Deluppgifter

Du ska skapa kod som söker svar på följande frågor:

* För hur många bostäder är postnumret 00700?
* För hur många bostäder är byggnadsåret på 2000‑talet?
* För hur många bostäder ligger boytan mellan 50 och 70 m²?
* Hur många av bostäderna har sålts minst en gång under åren 2010–2012?
* Vad är den dyraste bostadens försäljningspris?

## Inlämning

Rapporten ska innehålla din kod och de svar som koden ger på frågorna ovan.
