## Liste des évènement de l'entité `Company`

- ClientAccountCanceled  
case class ClientAccountCanceled(processUid: ProcessUid,
                                 aggregateUid: AggregateUid,
                                 sentDate: DateTime,
                                 canceledDate: LocalDate) extends OtherCompanyEvent

- ClientAccountReactivated  
case class ClientAccountReactivated(processUid: ProcessUid,
                                    aggregateUid: AggregateUid,
                                    sentDate: DateTime,
                                    reactivatedDate: LocalDate) extends OtherCompanyEvent
- ClientAccountUpdated  
case class ClientAccountUpdated(processUid: ProcessUid,
                                aggregateUid: AggregateUid,
                                holdingReference: Option[SafeUUID],
                                sentDate: DateTime,
                                updatedDate: LocalDate,
                                name: String) extends OtherCompanyEvent

- AgencyCreated

{  
  processUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  aggregateUid: [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  sentDate: [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  createdDate: [LocalDate](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#localdate),  
  agency: [Agency](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#agency)  
}  

- AgencyDeleted  
case class AgencyDeleted(processUid: ProcessUid,
                         aggregateUid: AggregateUid,
                         sentDate: DateTime,
                         deletedDate: LocalDate,
                         agencyUid: SafeAgencyUid) extends AgencyEvent

- AgencyUpdated  
case class AgencyUpdated(processUid: ProcessUid,
                         aggregateUid: AggregateUid,
                         sentDate: DateTime,
                         updatedDate: DateTime,
                         agency: RawAgency) extends AgencyEvent
