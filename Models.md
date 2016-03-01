## Models

### `SafeUUID`

Identifiant garanti unique en utilisant la norme (GUUID)[https://fr.wikipedia.org/wiki/Globally_Unique_Identifier]  
*Attention !* Si le format n'est pas bon, l'évènement sera rejeté.  
ex: `8074964f-c633-3c2a-055f-bbaf8ca8181b`

### `Option`

Signifie que le champ ainsi typé est optionnel. 
=> pas d'obligation de mettre le paramètre dans le json si absence de valeur.  
*Attention !* mettre `{ "field1":"coucou", "field2":"" }` est différent de `{ "field1":"coucou" }`

### `DateTime` [ISO-8601 calendar system](https://fr.wikipedia.org/wiki/ISO_8601)

`YYYY-MM-DDTHH:mm:ss+02:00` ex: `2016-02-29T12:03:32+02:00`

### `LocalDate` [ISO-8601 calendar system](https://fr.wikipedia.org/wiki/ISO_8601)

`YYYY-MM-DD` ex: `2016-02-29`

### `Agency`

{  
  "agencyUid": SafeUUID,  
  "name": String,  
  "extName": Option[String],  
  "address": Option[Address],  
  "phones": List[String],  
  "fax": Option[String],  
  "emails": List[String]  
}  
