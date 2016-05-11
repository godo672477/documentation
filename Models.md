## Models

### `SafeUUID`

Identifiant garanti unique en utilisant la norme [GUUID](https://fr.wikipedia.org/wiki/Globally_Unique_Identifier)  
*Attention !* Si le format n'est pas bon, l'évènement sera rejeté.  
ex: `8074964f-c633-3c2a-055f-bbaf8ca8181b`

### `List`

équivalent d'un array `[]`

### `Option`

Signifie que le champ ainsi typé est optionnel. 
=> pas d'obligation de mettre le paramètre dans le json si absence de valeur.  
*Attention !* mettre `{ "field1":"coucou", "field2":"" }` est différent de `{ "field1":"coucou" }`

### `DateTime`

[ISO-8601 calendar system](https://fr.wikipedia.org/wiki/ISO_8601)  
`YYYY-MM-DDTHH:mm:ss+02:00` ex: `2016-02-29T12:03:32+02:00`

### `LocalDate` 

[ISO-8601 calendar system](https://fr.wikipedia.org/wiki/ISO_8601)  
`YYYY-MM-DD` ex: `2016-02-29`

### `Agency`

{  
  "agencyUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "name": String,  
  "extName": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "address": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[[Address]](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#address),  
  "phones": [List](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#list)[String],  
  "fax": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "emails": [List](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#list)[String]  
}  

### `Address`

{  
  "quality": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "street": String,  
  "complement": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "zipCode": String,  
  "city": String,  
  "state": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "country": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String])  
}  

### `Name` *[enum]*
`Name` est une énumération, i.e le type peut avoir différentes valeurs : `data Name = CivilName | PoorName` 

{  
  "firstName": String,  
  "lastName": String,  
  "gender": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)["Male" || "Female"],  
  "nameType":"CivilName"  
}  

or

{  
  "value": String,  
  "nameType":"PoorName"  
}  

### `LocationReference` *[enum]*
`LocationReference` est une énumération, i.e le type peut avoir différentes valeurs :  
`data LocationReference = AgencyLocation`

{  
  "agencyUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "locationReferenceType":"AgencyLocation"  
}  

### `Operator` *[enum]*
`Operator` est une énumération, i.e le type peut avoir différentes valeurs :  
`data Operator = ReferencedOperator | AnonymousOperator`

{  
  "operatorUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "operatorType":"ReferencedOperator"  
}  

or

{  
  "name": String,  
  "operatorType":"AnonymousOperator"  
}  

### `TicketInfos`

{  
  "caller": [CallerType](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#callertype-enum),  
  "contactToCallback": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[[ContactToCallback]](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#contacttocallback-enum),  
  "claimNumber": [ClaimNumber](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#claimnumber-enum),  
  "address": [Address](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#address),  
  "request": String,  
  "instructions": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "callPurposeLabel": String,  
  "altCallPurpose": Map[String, List[String]],  
  "additionalData": Map[String, Option[String]]  
}  

### `CallerType` *[enum]*
`CallerType` est une énumération, i.e le type peut avoir différentes valeurs :  
`data CallerType = HumanCaller | AutomatonCaller`

{  
  "name": [Name](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#name-enum),  
  "medium": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[[ContactMedium]](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#contactmedium-enum),  
  "comment": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "callerType":"HumanCaller"
}  

or

`AutomatonCaller`

### `ContactToCallback` *[enum]*

### `ClaimNumber` *[enum]*

### `Persona` *[enum]*

### `ContactMedium` *[enum]*

### `Provider` *[enum]*

### `ProviderAssignationPurpose` *[enum]*

### `StillOnSite` *[enum]*
