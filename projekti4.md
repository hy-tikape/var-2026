---
title: Projektuppgift 4
permalink: /projekti4/
hide: true
---

# Projektuppgift 4

Skapa ett program som kan användas för att genomföra ett prestandatest på databasen. Delarna i prestandatestet är:

* Programmet skapar tabellen `Movies` som innehåller kolumnerna `id`, `name` och `release_year`.
* Programmet lägger till en miljon rader i tabellen. För varje film väljs en slumpmässig sträng på 8 tecken som namn och ett slumpmässigt heltal mellan 1900 och 2000 som år.
* Programmet kör tusen gånger en fråga som hämtar antalet filmer från år `x`. I varje fråga väljs `x` slumpmässigt mellan 1900 och 2000.

Skapa programmet så att alla rader läggs till inom samma transaktion (till exempel med kommandot `BEGIN` i början och `COMMIT` i slutet). På så sätt tar inte insättningen av rader för lång tid.

Vid beräkning av antalet filmer, använd en fråga som räknar antalet rader (`COUNT(*)`) som matchar villkoret.

Skapa tre funktioner i programmet som utför prestandatestet på följande sätt:

1. Tabellen får inte ha något index som påskyndar frågorna.
2. Ett index som påskyndar frågorna läggs till i tabellen innan raderna läggs in.
3. Ett index som påskyndar frågorna läggs till i tabellen innan frågorna körs.

Notera för varje test den tid som går åt för att lägga till rader och köra frågorna samt databasfilens storlek efter testet. Hur förklarar du testets resultat?

Kontrollera innan de faktiska testerna att dina frågor ger rimliga resultat: indexet bör påskynda frågorna avsevärt i testerna 2 och 3. Skriv under de faktiska testerna endast ut hur lång tid testerna tar, så att utskriften inte påverkar resultaten.

Kontrollera storleken på databasfilen efter att hela programmet har körts.

## Inlämning

Rapporten ska innehålla din kod och svar på följande frågor:

* Resultat från test 1:
  - Tid för att lägga till rader (i sekunder)
  - Tid för att köra frågorna (i sekunder)
  - Storleken på databasfilen efter testet (i megabyte)
* Resultat från test 2:
  - Tid för att lägga till rader (i sekunder)
  - Tid för att köra frågorna (i sekunder)
  - Storleken på databasfilen efter testet (i megabyte)
* Resultat från test 3:
  - Tid för att lägga till rader (i sekunder)
  - Tid för att köra frågorna (i sekunder)
  - Storleken på databasfilen efter testet (i megabyte)
* Hur förklarar du testets resultat?
