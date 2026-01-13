# Submission 08

## Aufgabe 1

```plantUML
@startuml

skinparam classAttributeIconSize 0

class PointOfSale {
  -id : Long
  -createdAt : LocalDateTime
  -updatedAt : LocalDateTime
  -name : String
  -description : String
  -type : String
  -campus : String
}

class Address {
  -street : String
  -houseNumber : String
  -postalCode : String
  -city : String
}

class User {
  -id : Long
  -createdAt : LocalDateTime
  -updatedAt : LocalDateTime
  -loginName : String
  -email : String
  -firstName : String
  -lastName : String
}

class Review {
  -id : Long
  -createdAt : LocalDateTime
  -updatedAt : LocalDateTime
  -text : String
  -approved : boolean
}

class OSMNode {
  -id : Long
}

PointOfSale "1" *-- "1" Address : has >
PointOfSale "1" <-- "0..*" Review : has >
User "1" <-- "0..*" Review : owns >
PointOfSale "0..1" <-- "0..*" OSMNode : imports >

@enduml
```

## Aufgabe 2

```plantUML
@startuml

object pos1{
  name = "Campus Café"
}

object osm1{
  id = 4711
}

object review1{
  text = "Sehr guter Kaffee!"
  approved = true
}

object user1
object user2
object user3

pos1 <-- review1
user1 <-- review1
user2 <-- review1
user3 <-- review1
pos1 <-- osm1

@enduml
```

## Aufgabe 3
s. aufgabe3.png

## Aufgabe 4

```plantUML
@startuml

[*] --> Entwurf

Entwurf : Bewertung wurde erstellt
Entwurf : Kann aktualisiert werden

Entwurf --> WartetAufGenehmigung : freigeben
Entwurf --> [*] : löschen

WartetAufGenehmigung : Wartet auf Genehmigungen
WartetAufGenehmigung : Kann aktualisiert werden

WartetAufGenehmigung --> WartetAufGenehmigung : genehmigen (< 3)
WartetAufGenehmigung --> Genehmigt : genehmigen (>= 3)
WartetAufGenehmigung --> Abgelehnt : ablehnen
WartetAufGenehmigung --> [*] : löschen

Genehmigt : Bewertung ist freigegeben
Genehmigt --> [*] : löschen

Abgelehnt : Bewertung wurde abgelehnt
Abgelehnt --> [*] : löschen

@enduml
```