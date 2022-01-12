.. _QueueMessages:

Queue Messages
==================================================================

Message will be sent to the state systems when we receive information back from NASWA.  The Messages will be published
onto an `AzureServiceBus <https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview>`_ queue.  The queues can be communicated with using `AMQP <https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol>`_. 


Earnings Verification Request Acknowledgement
#############################################
Consumes the ``EarningsVerificationRequestAcknowledgement`` message.

Earnings Verification Response
##############################
Consumes the ``EarningsVerificationResponseCollection`` message.

Separation Information Request Acknowledgement
##############################################
Consumes the ``SeparationInformationRequestAcknowledgement`` message.

Separation Information Response
###############################
Consumes the ``SeparationInformationResponseCollection`` message.