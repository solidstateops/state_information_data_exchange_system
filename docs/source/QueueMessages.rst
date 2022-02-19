.. _QueueMessages:

Queue Messages
==================================================================

Message will be sent to the state systems when we receive information back from NASWA.  The Messages will be published
onto an `AzureServiceBus <https://docs.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview>`_ queue.  The queues can be communicated with using `AMQP <https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol>`_. 


Earnings Verification Request Acknowledgement
#############################################
Consumes the ``EarningsVerificationRequestAcknowledgement`` message.

.. code-block:: csharp

    public async Task ProcessMessage(EarningsVerificationRequestAcknowledgement message)
    {
        var batchID = message.StateRequestFileGuid;

        //If success update the process date
        if (message.MessageCode == PostAcknowledgementMessageCode.FileSuccess)
        {
            // System should process successful messages
        }
        else if (message.MessageCode == PostAcknowledgementMessageCode.PartialSuccess)
        {
            for(var failedRequestRecord in message.FailedRequestRecords)
            {
                // System should process records that failed
            }                        
        }
        else
        {
            // System should process when the entire message fails
        }
    }

Earnings Verification Response
##############################
Consumes the ``EarningsVerificationResponseCollection`` message.

.. code-block:: csharp

    public async Task ProcessMessage(EarningsVerificationResponseCollection message)
    {
        foreach (var response in message.Responses)
        {
            if (response.RepeatableContract != null)
            {
                foreach (var contract in response.RepeatableContract)
                {
                    // System should handle RepeatableContracts
                }
            }
            if (response.RepeatableEarningsVerification != null)
            {
                foreach (var repeatableEarningsVerification in response.RepeatableEarningsVerification)
                {
                    // System should handle RepeatableEarningsVerifications
                }
            }
        }
    }

Separation Information Request Acknowledgement
##############################################
Consumes the ``SeparationInformationRequestAcknowledgement`` message.

.. code-block:: csharp

    public async Task ProcessMessage(SeparationInformationRequestAcknowledgement message)
    {
        var batchID = message.StateRequestFileGuid;
        Guid requestBatchGuid = message.StateRequestFileGuid;
        
        if(message.MessageCode == PostAcknowledgementMessageCode.FileSuccess)
        {
            // System should handle successful messages
        }
        else if(message.MessageCode == PostAcknowledgementMessageCode.PartialSuccess)
        {
            for(var failedRequestRecord in message.FailedRequestRecords)
            {
                // System should handle the failed records
            }
        }
        else
        {
            // System should handle when the whole message fails
        }
    }

Separation Information Response
###############################
Consumes the ``SeparationInformationResponseCollection`` message.

.. code-block:: csharp

    public async Task ProcessMessage(SeparationInformationResponseCollection message)
    {
        var sidesSeparationRequestId = message.SidesSeparationRequestID;

        foreach (SeparationInformationResponseRecord response in message.Responses)
        {           

            if (response.AmendedResponse != null)
            {
                // Handle Ammended Responses
            }
            if (response.Attachments != null)
            {
                foreach (var attachement in response.Attachments)
                {
                    // andle any attachements
                }
            }

            foreach (var remuneration in response.Remunerations)
            {
                // System should handle Remunerations
            }

            foreach (var priorIncident in response.PriorIncidents)
            {
                // System should handle PriorIncidents
            }

            foreach (var previousAssignments in response.PreviousAssignments)
            {
                // System should handle PerviousAssignments
            }

            foreach (var retirementAccounts in response.RetirementAccounts)
            {
                // System should handle the RetirementAccounts
            }

            foreach (var externalBusinessContractInformation in response.ExternalBusinessContactInformation)
            {
                // System should handle externalBusinessContractInformation
            }

            foreach (var witnessInformation in response.WitnessInformation)
            {
                // System should handle WitnessInformation
            }

            foreach (var item in response.FailedToReport)
            {
                // System should handle FailedToReport
            }
        }
    }
    
NotAcknowledged
###############################
Consumes the ``NotAcknowledged`` message.

.. code-block:: csharp

    public async Task ProcessMessage(NotAcknowledged message)
    {
        string messageType = message.MessageType;
        
        // MessageType will be one of 
        // EarningsVerificationRequestCollection,
        // EarningsVerificationRequestQuery,
        // SeparationInformationRequestCollection,
        // or SeparationInformationRequestQuery
        
        Exception exception = message.Exception;
        
        // Generic exception providing details of the error resulting in the NotAcknowledged
        // message being dispatched
        
        string correlationId = message.CorrelationId;
        
        // A globally unique identifier string to aid in the process of correlating the 
        // NotAcknowledged result to the originating request
        
        object Request = message.Request;

        // Generic obect containing the body of the originating message that has failed processing
    }
