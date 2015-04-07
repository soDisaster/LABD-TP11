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
Nous obtenons 6 résultats.


Question 3
----------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT  * WHERE{
 ?x humans:age ?t
FILTER (xsd:integer(?t) > 20)
}
```


Question 4.1
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT  * WHERE{
 ?x a humans:Person
 ?x humans:shoesize ?t
}
```

Question 4.2
------------
```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT  * WHERE{

 ?x a humans:Person
OPTIONAL {?x humans:shoesize ?s }
}
```


Question 4.3
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT  * WHERE{

 ?x a humans:Person
OPTIONAL {?x humans:shoesize ?s  FILTER (xsd:integer(?s )> 8 )}

}
```

Question 4.4
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT  * WHERE{

 ?x a humans:Person
FILTER EXISTS {?x humans:shoesize ?s  FILTER (xsd:integer(?s )> 8)}
FILTER EXISTS {?x humans:trouserssize ?t  FILTER (xsd:integer(?t )> 12)}
}
```

Question 5.1
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT * WHERE {
  ?x a humans:Person
  ?x  humans:name ?n
  ?x humans:shoesize ?s
  ?x humans:age ?a
 FILTER (?n ="John")
}
```

Question 5.2
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
DESCRIBE ?x
WHERE    {
  ?x  humans:name ?n
 FILTER (?n ="John") }

```

Question 6.1
------------

Harry père de John
John père de Mark
Jack père de Harry
Flora mère de Pierre
Cahterine mère de Lucas
Gaston père de Pierre
Gaston père de Jack
Laura mère de Catherine

si Parent siginifie père/mère et pas oncle/tante/cousin_germain

Sophie mère de John


Si nous ne prenons que hasChild nous avons :

Harry père de John
Jack père de Harry
Flora mère de Pierre
Gaston père de Pierre
Gaston père de Jack


Question 6.2
------------
```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT ?x WHERE
{
 ?x a humans:Person
?x humans:hasChild ?son



}
```

Question 6.3
------------

5 réponses 1 doublon (gaston)

```
<?xml version="1.0" ?>
<sparql xmlns='http://www.w3.org/2005/sparql-results#'>
<head>
<variable name='x'/>
</head>
<results>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs-instances#Flora</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs-instances#Gaston</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs-instances#Gaston</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs-instances#Harry</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs-instances#Jack</uri></binding>
</result>
</results>
</sparql>
```
Question 6.4
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT DISTINCT ?x WHERE
{
 ?x a humans:Person
?x humans:hasChild ?son

}
```
plus que 4 réponses

```
<?xml version="1.0" ?>
<sparql xmlns='http://www.w3.org/2005/sparql-results#'>
<head>
<variable name='x'/>
</head>
<results>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs-instances#Flora</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs-instances#Gaston</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs-instances#Harry</uri></binding>
</result>
<result>
<binding name='x'><uri>http://www.inria.fr/2007/09/11/humans.rdfs-instances#Jack</uri></binding>
</result>
</results>
</sparql>
```

Question 6.5
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT DISTINCT ?x WHERE
{
 ?x a humans:Man
FILTER NOT EXISTS {?x humans:hasChild ?son}

}
```

Question 6.6
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT DISTINCT ?x WHERE
{
 ?x a humans:Woman
?x humans:hasChild ?son
?x humans:hasSpouse ?somebody
}
```

Question 7
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT DISTINCT ?x ?y WHERE
{
 ?x a humans:Person
?y a humans:Person 
?x humans:shirtsize ?sx
?y humans:shirtsize ?sy

FILTER (?x != ?y)

FILTER (xsd:integer(?sx) = xsd:integer(?sy))
}
```
Gaston -John
Karl-Mark (ahah)
Karl-Pierre
Mark-Pierre


Question 8
----------

```
```

Question 9
----------

```

```
