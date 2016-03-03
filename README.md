# documentation
temporary public documentation for performance immo API

# API évènementielle

## Présentation rapide

Performance immo a fait le choix technique d'utiliser des API basées sur le protocole HTTP pour communiquer avec ses différents partenaires.   
Ainsi nous fournissons plusieurs API pour que nos partenaires puissent nous envoyer les informations nécessaire au fonctionnement de la plateforme avec leurs données clientes.

Aujourd'hui il existe 3 principales entités qui correspondent à 3 API :

- Pour renseigner les **Companies** (les comptes clients et leur agences) `/api/vEvent/companies`
- Pour renseigner les **contacts de fournisseur de service** `/api/vEvent/providerContacts`
- Pour renseigner les **Tickets** (ou dossiers) relatifs à un suivi de problème sur un patrimoine `/api/vEvent/tickets`

Précédemment, nous vous avons aprlé d'API évènementielle. Qu'est-ce que cela implique ?  

Au lieu de nous transmettre l'état des différentes entités (company, providerContact, ticket, ...), nous vous fournissons une interface mettant à disposition une liste d'évènements (ex: TicketOpened), associées à une entité donnée, vous permettant de nous envoyer un incrément de cet état.  
Pour expliquer cela autrement, la communication des données concernant une entité passe par la description d'une **cause** (un évènement) à un changement, plutôt que juste le changement lui-même.  

Nous vous fournissons, plus bas dans ce document, la liste des évènements (ainsi que le format de données pour chacun d'entre eux) pour chaque entités.

## Précisions sur les entités et sur leurs relations

Les 3 entités Ticket, Company & ProviderContact ont des liens entre elles.

Certains évènements de l'entité `Ticket` ont des dépendances vers les `Company` ou les `ProviderContact`, toujours dans ce sens.
Cela implique (nous verrons cela plus en détails dans la suite de ce document) de renseigner certaines informations des entités `ProviderContact` & `Company` avant d'envoyer des évènements sur l'entité `Ticket`.

## Le host des API

Le host (ou la base url) des API est spécifique à chaque client de performance immo.  
Pour connaitre votre host pour utiliser les API performance immo, addressez-vous à votre contact technique (sur votre fil slack de préférence).  
Toutes les API de performance immo sont uniquement accessible via `https`, garantissant un niveau de sécurité et de confidentialité minimum.  
Dans toutes la suite du document, nous ne préciserons que les path spécifiques à chaque action, sans rappeler à chaque fois le protocole  ou le host (`https://monapi.com`). Pensez-bien de votre côté à toujours rajouter ces informations dans vos requêtes.  
Chaque requête Http faite requiert l'envoi de json. N'oubliez pas de spécifier le header `Content-Type: application/json` dans chacune de vos requêtes.

## Authentification

Les API évènementielles de performance immo sont accessible uniquement à des utilisateurs authentifiés.
Chaque client de performance immo, se voit attribuer un couple `login / password` qui lui servira à s'authentifier.

`POST https://preprod.performance-immo.com/api/vEvent/login`

avec dans le body de la requête le json suivant :
```
{
   "login": "test",
   "password": "2Kz4exzL"
}
```

Cette requête retourne une réponse 200 avec un cookie nommé "PLAY_SESSION".  
Pour pouvoir utiliser ensuite les API évènementielle, il suffit de mettre ce cookie dans chacune de vos requêtes, en utilisant le Header `Cookie` comme valeur cookieName=cookieValue.  

`Cookie: PLAY_SESSION=cookieValue`

Cette session a par défaut une durée de vie de 12 h (il faut donc prévoir un mécanisme de reconnexion), et un idleTime de 1h (= si pas d'activité pendant 1h, la session expire).

## L'entité `Company`

### Création de l'entité

`POST    /api/vEvent/companies`

body

{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "holdingReference": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[SafeUUID],  
  "callCenterReference": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "createdDate": [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate),  
  "name": String,  
  "companyEventType":"ClientAccountCreated"  
}  

### Incrément de l'entité

`PATCH    /api/vEvent/companies/aggregateUid`

Dans le body, mettre l'évènement que vous souhaitez envoyer.

[liste des évènements pour l'entité `Company`](https://github.com/PerformanceIMMO/documentation/blob/master/CompanyEvents.md)

## L'entité `ProviderContact`

### Création de l'entité

`POST    /api/vEvent/providerContacts`

body

{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "date": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "name": [Name](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#name),  
  "phones": [List](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#list)[String],  
  "fax": [List](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#list)[String],  
  "emails": [List](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#list)[String]
  "eventType": "ProviderContactAdded"
}    

### Incrément de l'entité

`PATCH    /api/vEvent/providerContacts/aggregateUid`

Dans le body, mettre l'évènement que vous souhaitez envoyer.

[liste des évènements pour l'entité `ProviderContact`](https://github.com/PerformanceIMMO/documentation/blob/master/ProviderContactEvents.md)


## L'entité `Ticket`

### Création de l'entité

`POST    /api/vEvent/tickets`

body

{  
  processUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  aggregateUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  sentDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  locationRef: [LocationReference](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#locationreference-enum),  
  operator: [Operator](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#operator-enum),  
  ticket: [TicketInfos](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#ticketinfos),  
  openedDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime)  
}  

### Incrément de l'entité

`PATCH    /api/vEvent/tickets/aggregateUid`

Dans le body, mettre l'évènement que vous souhaitez envoyer.

[liste des évènements pour l'entité `Ticket`](https://github.com/PerformanceIMMO/documentation/blob/master/TicketEvent.md)
