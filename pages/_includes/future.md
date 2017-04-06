
## {{ page.title }}
-----------

####  Additional Development for a Robust Provider Directory

Throughout the development of the Argonaut Provider Directory several additional important items were reviewed for a robust Provider Directory. This page summarizes items under development, or things that should be considered for future efforts.

####  Provider Specialty, Provider Role, and Other Vocabularies

The Argonaut Provider Directory Implementation Guide uses NUCC for classification of the provider. The [Argonaut Provider Directory Provider Specialty (NUCC)](ValueSet-provider-specialty.html) and [Argonaut Provider Directory Provider Role (NUCC)](ValueSet-provider-role.html) value sets are included in this guide. The development team discussed the following limitations of NUCC:

-   Specialty Classification - NUCC isn't hierarchal and doesn't support the query 'return all cardiologists' without the creation of new value sets.
-   Missing Roles - There are several NUCC entries that don't include a generic 'Role' Classification. For example, 'Radiology' doesn't have a code.
-   Missing Specialties - 'Music Therapist' doesn't include any specialties. When this occurs, this guide recommends populating both Role and Specialty with same code.
-   Mapping - Many systems don't classify providers by NUCC in their clinical system. The use of NUCC, or another classification terminology, will require mapping for each system.

Additionally, other elements, such as Location.type, would benefit from a more robust value set. When a Provider Directory is balloted, all value sets should be reviewed.

####  Affiliate Relationships

A key aspect of Provider Directory is to describe relationships between two distinct organization and to track Affiliate Relationships.

Participants in the Argonaut PD development discussed the use of extensions, and profiles on the Basic resource since FHIR STU3 didn't include a logical resource. The development team, in conjunction with HL7 Patient Administration, proposed a new [OrganizationAffiliation Resource](http://wiki.hl7.org/index.php?title=OrganizationAffiliation_FHIR_Resource_Proposal). This Resource needs additional work to be included in a future FHIR build.

####  Formal HL7 Balloting

The Arognaut Provider Directory work group developed the content of this Implementation Guide thorugh a series of conference calls, listserv discussions, and connectathons. Two virtual connectathons were hosted, and two in conjunction with HL7.

The content in this guide is freely available to anyone.

A formal HL7 ballot provides an additional level of rigor, and a place for regulators to reference, for all industry participants. As part of the ballot additional examples, TestScripts, and conformance assessment of current servers should be considered. A Project Scope Statement is under discussion at HL7 under Project (GET APPROVAL NUMBER).

####  Provider Directory Operation

Healthcare facility and organization structures can be quite complex. In a future PD guide, the exact rules for walking the tree from location to organization, and a supporting operation should be considered.

####  Identifiers

There is not a unique code system, similar to NPI, for location identifiers. Additional work should be considered to develop a process to cross reference locations and organizations.

####  Next Steps

The Argonauts built the Provider Directory through regular calls, virtual and onsite connectathons, and collaboration with HL7. 

The above future items are important and should be considered for further development within existing industry efforts such as the ONC Directory Initiative, Sequoia CareQuality network, and other Vendor networks.  


