#### US Core AllergyIntolerance Profile


##### Scope and Usage

This profile sets minimum expectations for the [PractitionerRole](http://build.fhir.org/practitionerrole.html) resource to record, search and fetch allergies/adverse events associated with a patient.  It identifies the mandatory core elements, extensions, vocabularies and value sets which **SHALL** be present in the AllergyIntolerance resource when using this profile.  The requirements for the Argonaut Provider Directory data model were drawn from [IHE Healthcare Provider Directory](http://ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_HPD.pdf) and the [ONC Provider Directory Workshop](https://confluence.oncprojectracking.org/display/PDW/Workshop+Documents).


##### Mandatory Data Elements and Terminology


The following data-elements are mandatory (i.e data MUST be present). These are presented below in a simple human-readable explanation.  Profile specific guidance and an [example](#example) are provided as well.  The [**Formal Profile Definition**](#summary) below provides the  formal summary, definitions, and  terminology requirements.  

**Each PractitionerRole must have:**

1. An associated practitioner
1. An associated organization
1. A list of specialities
1. Contact information

**Profile specific implementation guidance:**

* The Practitioner resource SHALL be included when returning the PractitionerRole resource.
* The Endpoint resource SHALL be included when returning the PractitionerRole resource.
* The PractitionerRole.endpoint is where the [Direct address](https://www.healthit.gov/sites/default/files/directbasicsforprovidersqa_05092014.pdf) is included.
