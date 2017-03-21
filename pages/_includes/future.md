## Future Work
-----------

####  Additional Development for a Robust Provider Directory

Throughout the development of the Argonaut Provider Directory several additional important items were reviewed for a robust Provider Directory. This page summarizes those additional items and ongoing development.

####  Provider Speciality and Provider Role

The Argonaut Provider Directory Implementation Guide uses NUCC for classification of the provider. The [Argonaut Provider Directory Provider Speciality (NUCC)] and [Argonaut Provider Directory Provider Role (NUCC)] value sets are included in this guide. The development team discussed the folllowing limitations of NUCC:

-   Speciality Classification - NUCC isn't hierarchial and doesn't support the query 'return all cardiologists' without the creation of new value sets.
-   Missing Roles - There are several NUCC entries that don't include a generic 'Role' Classification. For example, 'Radiology' doesn't have a code.
-   Missing Specialities - 'Music Therapist' doesn't include any specialities. When this occurs, this guide recommends populating both Role and Speciality with same code. 
-   Mapping - Many systems don't classify providers by NUCC in their clinical system. The use of NUCC, or another classificaiton terminology, will require mapping for each system. 

####  Affiliate Relationships

A key aspect of Provider Directory is to describe relationships between two distinct organization and to track Affiliate Relationships.

Participants in the Argonaut PD development discussed the use of extensions, and profiles on the Basic resource since FHIR STU3 didn't include a logical resource. The development team, in conjunction with HL7 Patient Administration, proposed a new [OrganizationAffiliation Resource](http://wiki.hl7.org/index.php?title=OrganizationAffiliation_FHIR_Resource_Proposal). This Resource needs additional work to be included in a future FHIR build.

####  Formal HL7 Balloting	

The Arognuat Provider Directory work group developed the content of this Implementation Guide thorugh a series of conference calls, listserv discussions, and connectathons. Two virtual connectathons were hosted, and two in conjuntion with HL7. 

The content in this guide is freely available to anyone. 

A formal HL7 ballot provides an additional level of rigor, and a place for regulators to reference, for all industry participants. This is under discussion at HL7 under Project (GET APPROVAL NUMBER).


