## Liste des évènement de l'entité `Ticket`

- `TicketOpened`  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "locationRef": [LocationReference](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#locationreference-enum),  
  "operator": [Operator](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#operator-enum),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "ticket": [TicketInfos](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#ticketinfos),  
  "openedDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "eventType":"TicketOpened"  
}

- `CallEmittedTo`  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "operator": [Operator](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#operator-enum),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "recipient": [Persona](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#persona-enum),  
  "comment": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "medium": [ContactMedium](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#contactmedium-enum),  
  "date": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "eventType":"CallEmittedTo"  
}

- `CallReceived`  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "operator": [Operator](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#operator-enum),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "caller": String,  
  "callPurpose": String,  
  "comment": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "medium": [ContactMedium](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#contactmedium-enum),  
  "date": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "eventType":"CallReceived"  
}

- `ProviderAssigned`  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "operator": [Operator](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#operator-enum),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "provider": [Provider](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#provider-enum),  
  "purpose": [ProviderAssignationPurpose](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#providerassignationpurpose-enum),  
  "date": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "eventType":"ProviderAssigned"  
}

- `CallAnsweredByProvider`  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "operator": [Operator](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#operator-enum),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "provider": [Provider](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#provider-enum),  
  "comment": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "date": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "eventType":"CallAnsweredByProvider"  
}

- `CallNotAnsweredByProvider`  
{  
  "processUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "aggregateUid": [SafeUUID](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#safeuuid),  
  "operator": [Operator](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#operator-enum),  
  "sentDate": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "provider": [Provider](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#provider-enum),  
  "comment": [Option](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#option)[String],  
  "date": [DateTime](https://github.com/PerformanceIMMO/documentation/blob/master/Models.md#datetime),  
  "eventType":"CallNotAnsweredByProvider"  
}


case class AcceptMission(processUid: SafeUUID,
                         aggregateUid: SafeUUID,
                         provider: Provider,
                         comment: Option[String],
                         operator: Operator,
                         sentDate: DateTime,
                         date: DateTime) extends OtherTicketCommand

case class RefuseMission(processUid: SafeUUID,
                         aggregateUid: SafeUUID,
                         provider: Provider,
                         comment: Option[String],
                         operator: Operator,
                         sentDate: DateTime,
                         date: DateTime) extends OtherTicketCommand


case class ReopenTicket(processUid: SafeUUID,
                        aggregateUid: SafeUUID,
                        operator: Operator,
                        purpose: Option[String],
                        sentDate: DateTime,
                        date: DateTime) extends OtherTicketCommand

// Evènement générique du journal
case class AddLogTrial(processUid: SafeUUID,
                       aggregateUid: SafeUUID,
                       provider: Option[Provider],
                       operator: Operator,
                       sentDate: DateTime,
                       logTrial: LogTrial,
                       logTrialAddedDate: DateTime) extends OtherTicketCommand

case class AddMessage(processUid: SafeUUID,
                      aggregateUid: SafeUUID,
                      operator: Operator,
                      sentDate: DateTime,
                      message: String,
                      messageAddedDate: DateTime) extends OtherTicketCommand

case class CancelTicket(processUid: SafeUUID,
                        aggregateUid: SafeUUID,
                        operator: Operator,
                        sentDate: DateTime,
                        date: DateTime) extends OtherTicketCommand

case class ArriveOnSite(processUid: SafeUUID,
                        aggregateUid: SafeUUID,
                        provider: Provider,
                        operator: Operator,
                        sentDate: DateTime,
                        date: DateTime) extends OtherTicketCommand

case class GoFromSite(processUid: SafeUUID,
                      aggregateUid: SafeUUID,
                      provider: Provider,
                      operator: Operator,
                      sentDate: DateTime,
                      date: DateTime) extends OtherTicketCommand

case class StartIntervention(processUid: SafeUUID,
                             aggregateUid: SafeUUID,
                             startedDate: DateTime,
                             operator: Operator,
                             provider: Provider,
                             sentDate: DateTime) extends OtherTicketCommand

case class FinishIntervention(processUid: SafeUUID,
                              aggregateUid: SafeUUID,
                              finishedDate: DateTime,
                              operator: Operator,
                              provider: Provider,
                              sentDate: DateTime) extends OtherTicketCommand


sealed trait TicketClosingCommand extends OtherTicketCommand {
    def closingDate: DateTime
}

case class CloseTicket(processUid: SafeUUID,
                       aggregateUid: SafeUUID,
                       provider: Option[Provider],
                       brakedownNature: Option[String],
                       stillOnSite: StillOnSite,
                       report: Option[String],
                       result: Option[String],
                       operator: Operator,
                       sentDate: DateTime,
                       closingDate: DateTime) extends TicketClosingCommand

case class ArchiveTicket(processUid: SafeUUID,
                         aggregateUid: SafeUUID,
                         operator: Operator,
                         comment: Option[String],
                         sentDate: DateTime,
                         closingDate: DateTime) extends TicketClosingCommand

case class FixPermanently(processUid: SafeUUID,
                          aggregateUid: SafeUUID,
                          provider: Option[Provider],
                          brakedownNature: Option[String],
                          stillOnSite: StillOnSite,
                          report: Option[String],
                          operator: Operator,
                          sentDate: DateTime,
                          closingDate: DateTime) extends TicketClosingCommand

case class FixPartially(processUid: SafeUUID,
                       aggregateUid: SafeUUID,
                       provider: Option[Provider],
                       brakedownNature: Option[String],
                       stillOnSite: StillOnSite,
                       report: Option[String],
                       operator: Operator,
                       sentDate: DateTime,
                       closingDate: DateTime) extends TicketClosingCommand

case class CloseTicketImpossibleRepair(processUid: SafeUUID,
                                       aggregateUid: SafeUUID,
                                       provider: Option[Provider],
                                       brakedownNature: Option[String],
                                       stillOnSite: StillOnSite,
                                       report: Option[String],
                                       operator: Operator,
                                       sentDate: DateTime,
                                       closingDate: DateTime) extends TicketClosingCommand

case class PostponeFix(processUid: SafeUUID,
                       aggregateUid: SafeUUID,
                       provider: Option[Provider],
                       brakedownNature: Option[String],
                       stillOnSite: StillOnSite,
                       report: Option[String],
                       operator: Operator,
                       sentDate: DateTime,
                       closingDate: DateTime) extends TicketClosingCommand

case class CloseBeyondCallCenterScope(processUid: SafeUUID, aggregateUid: SafeUUID, operator: Operator, sentDate: DateTime, closingDate: DateTime) extends TicketClosingCommand
case class CloseAfterSeveralUnsuccessfulRecalls(processUid: SafeUUID, aggregateUid: SafeUUID, operator: Operator, sentDate: DateTime, closingDate: DateTime) extends TicketClosingCommand

case class UpdateTicket(processUid: SafeUUID,
                        aggregateUid: SafeUUID,
                        operator: Operator,
                        locationRef: LocationReference,
                        ticket: TicketInfos,
                        sentDate: DateTime,
                        date: DateTime) extends OtherTicketCommand
