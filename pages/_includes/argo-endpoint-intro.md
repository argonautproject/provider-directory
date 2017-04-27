##### Scope and Usage

This profile sets minimum expectations for the [Endpoint]({{ site.data.fhir.path }}/endpoint.html) resource to record, search and fetch an Endpoint associated with a Provider or Organization.  It identifies the mandatory core elements, extensions, vocabularies and value sets which **SHALL** be present in the Endpoint resource when using this profile.  The requirements for the Argonaut Provider Directory data model were drawn from [IHE Healthcare Provider Directory](http://sihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_HPD.pdf) and the [ONC Provider Directory Workshop](https://confluence.oncprojectracking.org/display/PDW/Workshop+Documents).


##### Mandatory Data Elements and Terminology


The following data-elements are mandatory (i.e data MUST be present). These are presented below in a simple human-readable explanation.  Profile specific guidance and examples are provided as well.  The [**Formal Profile Definition**](#summary) below provides the  formal summary, definitions, and  terminology requirements.  

**Each Endpoint must have:**

1. A status
1. A name
1. A managing organization
1. The channel type to send notifications on (connectionType)
1. The address

**Profile specific implementation guidance:**

* None

##### Examples

- [Endpoint-1](Endpoint-example-endpoint-1.html)
- [Endpoint-2](Endpoint-example-endpoint-2.html)
