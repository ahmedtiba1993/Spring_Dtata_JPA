# Spring_Dtata_JPA
Dans cet exemple, vous comprendrez ce qu'est Spring Data JPA et comment transformer une base de données ou un diagramme de classes en une application Spring . il capable de gérer toutes vos tables de base de données.
Vous apprendrez quelles annotations utiliser comme Column, Entity, Table Id, GeneratedValue.
Vous apprendrez à rendre une colonne non nulle, unique, donnez-lui un nom spécifique

# Ajout de Spring Data JPA dans un projet Maven
Spring Data se compose d’un noyau central et de plusieurs sous modules dédiés à un type de système de stockage et une technologies d’accès. Dans un projet Maven, pour utiliser Spring Data pour une base de données relationnelles avec JPA, il faut déclarer la dépendance suivante :
```
<dependency>
  <groupId>org.springframework.data</groupId>
  <artifactId>spring-data-jpa</artifactId>
  <version>2.2.2.RELEASE</version>
</dependency>
```
# Les entités

![Diagramme sans nom drawio](https://user-images.githubusercontent.com/72476268/211169548-f83108c9-f230-4d74-9806-0f27aae596cb.png)

# Le mapping entre le bean entité et la table

L'API propose plusieurs annotations pour supporter un mapping O/R assez complet.
Annotation	Rôle
- @jakarta.persistence.Table	: Préciser le nom de la table concernée par le mapping
- @jakarta.persistence.Column	: Associer un champ de la table à la propriété (à utiliser sur un getter)
- @jakarta.persistence.Id	: Associer un champ de la table à la propriété en tant que clé primaire (à utiliser sur un getter)
- @jakarta.persistence.GeneratedValue	: Demander la génération automatique de  la clé primaire au besoin

L'annotation @jakarta.persistence.Table permet de lier l'entité à une table de la base de données. Par défaut, l'entité est liée à la table de la base de données correspondant au nom de la classe de l'entité. Si ce nom est différent alors l'utilisation de l'annotation @Table est obligatoire. C'est notamment le cas si des conventions de nommage des entités de la base de données sont mises en place.

L'annotation @Table possède plusieurs attributs , parmi ces annotation : 
- Attributs **name** : Nom de la table

L'annotation @jakarta.persistence.Column permet d'associer un membre de l'entité à une colonne de la table. Par défaut, les champs de l'entité sont liés aux champs de la table dont les noms correspondent. Si ces noms sont différents alors l'utilisation de l'annotation @Column est obligatoire. C'est notamment le cas si des conventions de nommage des entités de la base de données sont mises en place.

L'annotation @Column possède plusieurs attributs :
- name : Nom de la colonne
- unique : Indique si la colonne est unique
- nullable : Indique si la colonne est nullable
- length : Indique la taille d'une colonne de type chaîne de caractères
- precision : Indique la taille d'une colonne de type numérique

La clé primaire peut être générée automatiquement en utilisant l'annotation @jakarta.persistence.GeneratedValue. 

Cette annotation possède plusieurs attributs :
- strategy : Précise le type de générateur à utiliser : TABLE, SEQUENCE, IDENTITY ou AUTO. La valeur par défaut est AUTO
generator : Nom du générateur à utiliser

Le type AUTO est le plus généralement utilisé : il laisse l'implémentation générer la valeur de la clé primaire.

Le type IDENTITY utilise un type de colonne spécial de la base de données.


