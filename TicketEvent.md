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

case class EmitCallTo(processUid: SafeUUID,
                      aggregateUid: SafeUUID,
                      operator: Operator,
                      recipient: Persona,
                      comment: Option[String],
                      medium: ContactMedium,
                      sentDate: DateTime,
                      date: DateTime) extends OtherTicketCommand

case class ReceiveCall(processUid: SafeUUID,
                       aggregateUid: SafeUUID,
                       caller: String,
                       callPurpose: String,
                       operator: Operator,
                       comment: Option[String],
                       medium: ContactMedium,
                       sentDate: DateTime,
                       date: DateTime) extends OtherTicketCommand

case class AssignProvider(processUid: SafeUUID,
                          aggregateUid: SafeUUID,
                          operator: Operator,
                          provider: Provider,
                          purpose: ProviderAssignationPurpose,
                          date: DateTime,
                          sentDate: DateTime) extends OtherTicketCommand

case class ProviderAnswerCall(processUid: SafeUUID,
                              aggregateUid: SafeUUID,
                              provider: Provider,
                              operator: Operator,
                              comment: Option[String],
                              sentDate: DateTime,
                              date: DateTime) extends OtherTicketCommand

case class ProviderNotAnswerCall(processUid: SafeUUID,
                                 aggregateUid: SafeUUID,
                                 provider: Provider,
                                 operator: Operator,
                                 comment: Option[String],
                                 sentDate: DateTime,
                                 date: DateTime) extends OtherTicketCommand

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
