

# Constructor

On liste toute les commandes qui réalisent ...

## rdfs2
Action : 

## rdfs3
Action : Si le range d'une propriété est connue, ajoute sa valeur comme type des objets.

Exemple : Gaston en tant que ami de David devrait être du type Person

Triplets : 
- i:David h:hasFriend i:Gaston ;
- h:hasFriend rdfs:range h:Person ;

Code :
```{rdf}
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> .
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#> .

construct {
  ?o rdf:type ?t .
}
where {
  ?p rdfs:range ?t .
  ?s ?p ?o .
}
```

```{rdf}
@prefix h: <http://www.inria.fr/2007/09/11/humans.rdfs#> .
@prefix i: <http://www.inria.fr/2007/09/11/humans.rdfs-instances#> .

select ?o ?t where {
  ?s h:hasSpouse ?o
  ?o rdf:type ?t
  filter (?o = i:Gaston)
}
``` 	

## rdfs4