# LABD-TP11

Authors
-------

- Thibault Rosa
- Anne-Sophie Saint-Omer

Exercice 1
----------

Question 1
----------

Cela retourne tout les x de type t

Tous les triplets de définition de type.

```
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs-instances#John</uri></binding>
<binding name='t'><uri>http://www.inria.fr/2007/09/11/humans.rdfs#Person</uri></binding>
</result>
```

Nous obtenons 33 résultats car SPARQL prend en compte les triplets inférés.


Question 2
----------

Cette requête affiche pour résultats les personnes qui sont mariés.
Nosu obtenons 6 résultats.


Question 3
----------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT  * WHERE{
 ?x humans:age ?t
FILTER (xsd:integer(?t) > 20)
}
```


Question 4
----------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT  * WHERE{
 ?x humans:shoesize ?t
}
```




