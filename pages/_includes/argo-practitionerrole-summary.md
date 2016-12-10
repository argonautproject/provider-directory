#### Summary of the Mandatory Requirements 

1.  One practitioner in `PractitionerRole.practitioner`
1.  One organization in `PractitionerRole.organization`
1.  One practitioner role code in `PractitionerRole.code" which has an [extensible](http://build.fhir.org/terminologies.html#extensible) binding to:
    -    [NUCC - Classification](ValueSet-provider-role.html) value set
1.  One practitioner specialty code in `PractitionerSpecialty.code" which has an [extensible](http://build.fhir.org/terminologies.html#extensible) binding to:
    -    [NUCC - Specialization](ValueSet-provider-specialty.html) value set
1.  One reference to a location in `PractitionerRole.location`
1.  At least one contact using either 'PractitionerRole.telecom' OR or reference to an EndPoint Resource in  `PractitionerRole.endpoint`
  