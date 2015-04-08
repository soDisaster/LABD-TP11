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

Propriété hasFather : 
 - John est le père de Mark.


Propriété hasMother : 
 -Catherine est la mère de Lucas.

Propriété hasChild nous avons :

-Harry est le père de John.
-Jack est le père de Harry.
-Flora est le mère de Pierre.
-Gaston est le père de Pierre.
-Gaston est le père de Jack.
-Laura est la mère de Catherine.


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

5 réponses dont 1 doublon, Gaston

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
?x humans:hasChild ?children

}
```
Plus que 4 réponses

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
FILTER NOT EXISTS {?x humans:hasChild ?children}

}
```

Question 6.6
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT DISTINCT ?x WHERE
{
?x a humans:Woman
OPTIONAL {?x humans:hasChild ?children}
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
- Gaston et John 
- Karl et Mark 
- Karl et Pierre
- Mark et Pierre


Question 8
----------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT DISTINCT ?friend ?x WHERE
{
?x humans:hasFriend ?friend
}
```

Question 9
----------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT DISTINCT * WHERE
{
?x a humans:Woman
}
```


Exercice 2
----------


Question 2
----------

```
SELECT DISTINCT ?class 
WHERE {
   ?class rdf:type rdfs:Class.
}
````


Question 3
----------

````
SELECT *
 WHERE {
     ?subject rdfs:subClassOf ?s
 }
```


Question 4
----------

Encore un problème 
```
SELECT *
WHERE {
  ?class rdf:type rdf:Property .
  ?class rdfs:comment ?c
 ?class rdf:ID ?i
 FILTER(?i = "shoesize")
}
```


Question 5
----------

Encore un problème

?class rdf:ID ?i
FILTER(?i = "Person")
?x xml:lang ?l
FILTER(?l = "fr")


Question 6
----------



Exercice 3
----------

Question 1.1
-----------
```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT DISTINCT ?x WHERE
{
?x a humans:Person
}
```

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT DISTINCT ?x WHERE
{
?x a humans:Animal
}
```

Question 1.2
------------

Il a y beaucoup plus de résultats. Person avec rdfs comprend aussi Man et Woman.
Il en est de même pour Animal qui comprend Person.

Question 2.1
------------

```
PREFIX humans: <http://www.inria.fr/2007/09/11/humans.rdfs#>
SELECT DISTINCT *  WHERE
{
?x a humans:Man
?x humans:hasSpouse ?y
}
```

Nous avons un seul resultat car les autres sont déclaré comme Person et non Man

Question 2.2
------------

Rien à changé ...






