---
title: Projektuppgift 3
permalink: /projekti3/
hide: true
---

# Projektuppgift 3

I de följande testerna används en SQLite-tabell som har skapats på följande sätt:

```sql
CREATE TABLE Test (x INTEGER);
INSERT INTO Test (x) VALUES (1);
```

I testet visas kommandona som körs i två transaktioner i ordning. K1 är kommandot från användare 1 och K2 är kommandot från användare 2. Testa kommandona genom att öppna två SQLite-tolkar mot samma databasfil.

Din uppgift är att ange vilket svar `SELECT`-frågorna ger och om transaktionerna lyckas. En transaktion lyckas om alla kommandon i den genomförs (utan felmeddelandet `Error: database is locked`).

## Test 1

```
K1: BEGIN;
K1: SELECT x FROM Test;

K2: BEGIN;
K2: UPDATE Test SET x = 2;
K2: SELECT x FROM Test;
K2: COMMIT;

K1: COMMIT;
```

## Test 2

```
K1: BEGIN;
K1: SELECT x FROM Test;
K1: UPDATE Test SET x = 2;

K2: BEGIN;
K2: SELECT x FROM Test;
K2: COMMIT;

K1: COMMIT;
```

## Test 3

```
K1: BEGIN;
K1: UPDATE Test SET x = 2;

K2: BEGIN;
K2: UPDATE Test SET x = 3;
K2: SELECT x FROM Test;
K2: COMMIT;

K1: SELECT x FROM Test;
K1: COMMIT;
```

## Test 4

```
K1: BEGIN;
K1: UPDATE Test SET x = 2;

K2: BEGIN;
K2: UPDATE Test SET x = 2;
K2: SELECT x FROM Test;
K2: COMMIT;

K1: SELECT x FROM Test;
K1: COMMIT;
```

## Test 5

```
K1: BEGIN;
K1: SELECT x FROM Test;

K2: BEGIN;
K2: SELECT x FROM Test;
K2: UPDATE Test SET x = 2;
K2: COMMIT;

K1: UPDATE Test SET x = 2;
K1: COMMIT;
```

## Inlämning

Rapporten ska för varje test innehålla följande:

* Vilket svar ger 1. transaktionens `SELECT`-fråga?
* Vilket svar ger 2. transaktionens `SELECT`-fråga?
* Lyckas transaktion 1?
* Lyckas transaktion 2?
* Hur förklarar du dessa resultat?
