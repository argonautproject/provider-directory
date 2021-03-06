## {{ page.title }}
{:.no_toc}

{% include publish-box.html %}

The Argonaut project Provider Directory guide is based upon the [FHIR STU3 API]({{ site.data.fhir.path }}) and contains the foundation for a robust provider directory. It describes the use cases and search expectations for finding a practitioner or organization. It outlines the key data elements for any provider directory and basic query guidance. The components developed in this guide are intended to provide a foundation for a central or distributed Provider or Healthcare Directory. Additional work flow components and elements may be required for a particular implementation.

The requirements for the Argonaut Provider Directory data model were drawn from [IHE Healthcare Provider Directory] and the [ONC Provider Directory Workshop].


#### Use Cases

1.  Search for Practitioner by demographics
    -   Name
    -   Specialty

2.  Search for Practitioner within a region (city, state)
    -   Practitioner or specialty within a specified distance - 10 miles from patient home
    -   Show me every one of this specialty in the city

3.  Search for Organization and facility by:
    -   Name
    -   Address

4.  Search for Practitioner by organizational relationships
    -   Practitioner in a specific health organization (e.g. Baptist Health Organization)
    -   Practitioner in a specific clinic (e.g. West Clinic)

Example Searches

1.  Locate a Provider's Direct address
    1.  Search Practitioner by Name or Specialty
    2.  Select appropriate Practitioner
    3.  Retrieve Direct address from PractitionerRole.endpoint

2.  Locate a Provider's phone or fax number at a location
    1.  Search Practitioner by Name or Specialty
    2.  Select appropriate Practitioner
    3.  Retrieve PractitionerRole.telecom with PractitionerRole.telecom.system=phone\|fax

#### Assumptions and Preconditions

Electronic service information will be available when the Practitioner or Organization is returned

Additional implementation guidance on the use cases and core data elements will be required. For example:

-   Pushing updates to central directory
-   Bulk registry download

#### Profiles
  {%  include list-simple-profiles.xhtml %}

#### Value Sets
  {% include list-simple-valuesets.xhtml %}
  
------------------------------------------------------------------------
Author: Brett Marquard

Author: Eric Haas

  [IHE Healthcare Provider Directory]: http://ihe.net/uploadedFiles/Documents/ITI/IHE_ITI_Suppl_HPD.pdf
  [ONC Provider Directory Workshop]: https://confluence.oncprojectracking.org/display/PDW/Workshop+Documents
