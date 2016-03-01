# documentation
temporary public documentation for performance immo API

## API évènementielle

### Présentation rapide

Performance immo a fait le choix technique d'utiliser des API basée sur le protocole HTTP pour communiquer avec ses différents partenaires.   
Ainsi nous fournissons plusieurs API pour que nos partenaires puissent nous envoyer les informations nécessaire au fonctionnement de la plateforme avec leurs données clientes.

Aujourd'hui il existe 3 principales API :

- Pour renseigner les Companies (les comptes clients et leur agences) `/api/vEvent/companies`
- Pour renseigner les contacts de fournisseur de service `/api/vEvent/providerContacts`
- Pour renseigner les tickets (ou dossiers) relatifs à un suivi de problème sur un patrimoine `/api/vEvent/tickets`
