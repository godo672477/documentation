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
  "contactToCallback": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[[ContactToCallback]](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#contacttocallback),  
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

### `ContactToCallback`

{  
  "name": String,  
  "medium": [ContactMedium](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#contactmedium-enum),  
  "availability": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[[DateTime]](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "comment": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String]  
}  

### `ClaimNumber`

{  
  "callCenterClaimNumber": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "clientClaimNumber": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String]  
}  

### `Persona` *[enum]*
`Persona` est une énumération, i.e le type peut avoir différentes valeurs :  
`data Persona = UnClassifiedPersona | ProviderPersona`

{  
  "name": [Name](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#name-enum),  
  "status": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "callPurpose": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "personaType":"UnClassifiedPersona"  
}  

or  

{  
  "provider": [Provider](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#provider-enum),  
  "personaType":"ProviderPersona"  
}  

### `ContactMedium` *[enum]*
`ContactMedium` est une énumération, i.e le type peut avoir différentes valeurs :  
`data ContactMedium = Phone | Fax | Mail | SMS`

{  
  "phone": String,  
  "contactMediumType":"Phone"  
}  

or

{  
  "fax": String,  
  "contactMediumType":"Fax"  
}  

or

{  
  "mail": String,  
  "contactMediumType":"Mail"  
}  

or

{  
  "phone": String,  
  "contactMediumType":"SMS"  
}  


### `Provider` *[enum]*
`Provider` est une énumération, i.e le type peut avoir différentes valeurs :  
`data Provider = ReferencedProvider | AnonymousProvider`

{  
  "providerUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "providerType":"ReferencedProvider"  
}  

or

{  
  "name": [Name](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#name-enum),  
  "phones": [List](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#list)[String],  
  "fax": [List](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#list)[String],  
  "emails": [List](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#list)[String],  
  "providerType":"AnonymousProvider"  
}

### `ProviderAssignationPurpose` *[enum]*
`ProviderAssignationPurpose` est une énumération, i.e le type peut avoir différentes valeurs :  
`data ProviderAssignationPurpose = RecourseChanged | Purpose`

{  
  "purpose": String,  
  "providerAssignationPurposeType":"Purpose"  
}  

or

{  
  "comment": String,  
  "providerAssignationPurposeType":"RecourseChanged"  
}

### `StillOnSite` *[enum]*
`StillOnSite` est une énumération, i.e le type peut avoir différentes valeurs :  
`data StillOnSite = Yes | No | NotAsked | ProviderRefuseToReply | NA`
