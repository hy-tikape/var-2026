---
title: Projektuppgift 5
permalink: /projekti5/
hide: true
---

# Projektuppgift 5

Din uppgift är att skapa kod som gör det möjligt att definiera relationer och utföra operationer i relationsalgebra, såsom projektion och selektion. Koden ska möjliggöra följande funktioner:

* Skapa en ny relation som innehåller de angivna attributen.
* Lägga till en ny tupel (tuple) i relationen
* Skriv ut tuplerna som finns i relationen
* Skapa en ny relation med hjälp av projektionsoperationen när det önskade attributen anges
* Skapa en ny relation med hjälp av selektionsoperationen när det önskade attributvärdet anges

Du kan anta att jämförelsen i implementeringen av selektionsoperationen alltid är av typen `=`, det vill säga operationen behöver inte tillåta andra jämförelseformer.

## Testa koden (Python)

Följande kod testar Python-koden:

```python
products = Relation(("id", "name", "price"))

products.add_tuple((1, "rädisa", 7))
products.add_tuple((2, "morot", 5))
products.add_tuple((3, "rova", 4))
products.add_tuple((4, "kålrot", 8))
products.add_tuple((5, "selleri", 4))

print(products)

print(projection(products, ("name")))
print(projection(products, ("price")))
print(projection(products, ("name", "price")))

print(restriction(products, "name", "morot"))
print(restriction(products, "price", 4))

print(projection(restriction(products, "price", 4), ("name")))
```

Kodens resultat ska se ut på ungefär följande sätt:

```
{(1, 'rädisa', 7), (2, 'morot', 5), (3, 'rova', 4), (5, 'selleri', 4), (4, 'kålrot', 8)}
{('kålrot',), ('selleri',), ('rädisa',), ('rova',), ('morot',)}
{(7,), (8,), (4,), (5,)}
{('kålrot', 8), ('selleri', 4), ('rädisa', 7), ('rova', 4), ('morot', 5)}
{(2, 'morot', 5)}
{(3, 'rova', 4), (5, 'selleri', 4)}
{('rova',), ('selleri',)}
```

## Testa koden (R)

Följande kod testar R-koden:

```r
products <- Relation(c("id", "name", "price"))

products <- add_tuple(products, c(1, "rädisa", 7))
products <- add_tuple(products, c(2, "morot", 5))
products <- add_tuple(products, c(3, "rova", 4))
products <- add_tuple(products, c(4, "kålrot", 8))
products <- add_tuple(products, c(5, "selleri", 4))

print(products)

print(projection(products, c("name")))
print(projection(products, c("price")))
print(projection(products, c("name", "price")))

print(restriction(products, "name", "morot"))
print(restriction(products, "price", 4))

print(projection(restriction(products, "price", 4), c("name")))
```

Kodens resultat ska se ut på ungefär följande sätt:

```
  id    name  price
1  1  rädisa      7
2  2   morot      5
3  3    rova      4
4  4  kålrot      8
5  5 selleri      4

     name
1  rädisa
2   morot
3    rova
4  kålrot
5 selleri

  price
1     7
2     5
3     4
4     8

      name price
1   rädisa     7
2    morot     5
3     rova     4
4   kålrot     8
5  selleri     4

  id     name price
2  2    morot     5

  id    name price
3  3    rova     4
5  5 selleri     4

     name
3    rova
5 selleri
```

## Inlämning

Rapporten ska innehålla din kod.
