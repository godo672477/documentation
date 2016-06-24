## Liste des évènement de l'entité `Company`

- CancelClientAccount  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "canceledDate": [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate),  
  "commandType":"CancelClientAccount"  
}  

- ReactiveClientAccount  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "reactivatedDate": [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate)    
  "commandType":"ReactiveClientAccount"
}  

- UpdateClientAccount  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "holdingReference": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[[SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid)],    
  "updatedDate": [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate),   
  "name": String
  "commandType":"UpdateClientAccount"
}

- CreateAgence  
{  
  processUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  aggregateUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  sentDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  createdDate: [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate),  
  agency: [Agency](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#agency),  
  commandType:"CreateAgence"  
}  

- DeleteAgence  
{  
  processUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  aggregateUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  sentDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  deletedDate: [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate),  
  agencyUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  commandType:"DeleteAgence"    
}  

- UpdateAgence  
{  
  processUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  aggregateUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  sentDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  updatedDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  agency: [Agency](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#agency),  
  commandType:"UpdateAgence"    
}
