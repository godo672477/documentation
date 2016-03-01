# documentation
temporary public documentation for performance immo API

## API évènementielle

### Présentation rapide

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

### Précisions sur les entités et sur leurs relations

Les 3 entités Ticket, Company & ProviderContact ont des liens entre elles.

Certains évènements de l'entité `Ticket` ont des dépendances vers les `Company` ou les `ProviderContact`, toujours dans ce sens.
Cela implique (nous verrons cela plus en détails dans la suite de ce document) de renseigner certaines informations des entités `ProviderContact` & `Company` avant d'envoyer des évènements sur l'entité `Ticket`.

### Le host des API

Le host (ou la base url) des API est spécifique à chaque client de performance immo.  
Pour connaitre votre host pour utiliser les API performance immo, addressez-vous à votre contact technique (sur votre fil slack de préférence).  
Toutes les API de performance immo sont uniquement accessible via `https`, garantissant un niveau de sécurité et de confidentialité minimum.  
Dans toutes la suite du document, nous ne préciserons que les path spécifique à chaque action, sans rappeler à chaque fois le protocole  ou le host (`https://monapi.com`). Pensez-bien de votre côté à toujours rajouter ces informations dans vos requêtes.

### Authentification

Les API évènementielles de performance immo sont accessible uniquement à des utilisateurs authentifiés.
Chaque client de performance immo, se voit attribuer un couple `login / password` qui lui servira à s'authentifier.

`POST https://preprod.performance-immo.com/api/vEvent/login`

avec dans le body de la requête le json suivant :
```
{
   "login": "test",
   "password": "anstel"
}
```

Cette requête retourne une réponse 200 avec un cookie nommé "PLAY_SESSION".  
Pour pouvoir utiliser ensuite les API évènementielle, il suffit de mettre ce cookie dans chacune de vos requêtes, en utilisant le Header `Cookie` comme valeur cookieName=cookieValue.  

`Cookie: PLAY_SESSION=cookieValue`

Cette session a par défaut une durée de vie de 12 h (il faut donc prévoir un mécanisme de reconnexion), et un idleTime de 1h (= si pas d'activité pendant 1h, la session expire).

### L'entité `Company`

Création de l'entité
