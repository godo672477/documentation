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

### L'entité `Company`
