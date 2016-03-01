## Liste des évènement de l'entité `Company`

- ClientAccountCanceled  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "canceledDate": [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate),  
  "companyEventType":"ClientAccountCanceled"  
}  

- ClientAccountReactivated  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "reactivatedDate": [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate)    
  "companyEventType":"ClientAccountCanceled"
}  

- ClientAccountUpdated  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "holdingReference": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[[SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid)],    
  "updatedDate": [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate),   
  "name": String
  "companyEventType":"ClientAccountUpdated"
}

- AgencyCreated
{  
  processUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  aggregateUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  sentDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  createdDate: [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate),  
  agency: [Agency](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#agency)  
}  

- AgencyDeleted  
{  
  processUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  aggregateUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  sentDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  deletedDate: [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate),  
  agencyUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid)  
}  

- AgencyUpdated  
{  
  processUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  aggregateUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  sentDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  updatedDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  agency: [Agency](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#agency)  
}
