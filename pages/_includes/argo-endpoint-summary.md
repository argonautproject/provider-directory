#### Summary of the Mandatory Requirements 

1.  One status code in `Endpoint.status` which has a [required]({{ site.data.fhir.path }}/terminologies.html#required) binding to:
    -    [EndpointStatus]({{ site.data.fhir.path }}/valueset-endpoint-status.html) value set
1.  One name in `Endpoint.name`
1. One reference to a managing organization in `Endpoint.managingOrganization`
1.  One channel type code in `Endpoint.connectionType` which has an [required]({{ site.data.fhir.path }}/terminologies.html#required) binding to:
    -    [SubscriptionChannelType]({{ site.data.fhir.path }}/valueset-subscription-channel-type.html) value set
1.  One address in `Endpoint.address`
1.  One payload type code in `Endpoint.payloadType` which has an [extensible]({{ site.data.fhir.path }}/terminologies.html#extensible) binding to:
    -    [Endpoint Payload Type]({{ site.data.fhir.path }}/valueset-endpoint-payload-type.html) value set.
