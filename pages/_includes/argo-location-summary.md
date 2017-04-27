#### Complete Summary of the Mandatory Requirements

1. A `Location.status` which has an [required]({{ site.data.fhir.path }}/terminologies.html#required) binding to:
   -   [LocationStatus]  value set.
1. A `Location.name`
1. A `Location.telecom`
1. A `Location.address`
1. A `Location.managingOrganization`

Each Location SHOULD have:

1. A `Location.type`
 - The Location.type must come from value set?
1. At least one identifier in `Location.identifier`
 - NPI preferred
 - Tax id is allowed
 - Local id is allowed in addition to 'authoritative' identifier
1. A `Location.endpoint`





[LocationStatus]: {{ site.data.fhir.path }}/valueset-location-status.html
