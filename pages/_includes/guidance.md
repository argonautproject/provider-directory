## {{ page.title }}
{:.no_toc}


<!-- TOC  the css styling for this is \pages\assets\css\project.css under 'markdown-toc'-->

* Do not remove this line (it will not be displayed)
{:toc}

<!-- end TOC -->

This section provides specific guidance for implementing the Argonaut Provider Directory guide.  The conformance verbs used are defined in [FHIR Conformance Rules]({{ site.data.fhir.path }}/conformance-rules.html#conflang).


source pages/\_include/{{page.md_filename}}.md  file

### Background on the PD Resource Relationships

#### Relationships between Practitioner, Organization, Location, and Endpoints
{:.no_toc}

This IG describes the basic resources and required elements to form a robust Provider Directory. During the development of the guide, the team discussed the relationships between resources and drafted several diagrams. Figure 1 is a basic diagram of single provider practice. The Practitioner has an Endpoint for Direct messaging, and the Organization has a Lab Endpoint for results.

{% include img.html img="Single-provider-practice.png" caption="Figure 1: Single Provider Practice" %}

Figure 2 represents a single practitioner working at multiple locations with different parent organizations. The Practitioner has an Endpoint, Direct address, at each Organization. The separate Organizations have their own Endpoints for Lab results.

{% include img.html img="Multi-organization-practitioner.png" caption="Figure 2: Provider Practicing at Multiple Organizations" %}

Figure 3 represents multiple practitioners practicing at multiple locations within a single Organization. The Practitioner has an Endpoint, Direct address, at each Organization.

{% include img.html img="Multi-Location-provider-practice.png" caption="Figure 3: Providers Practicing at Multiple Locations" %}

Figure 4 adds a parent organization to Figure 2. The single parent organization presides over the two sub-organizations and does not have a Location.

{% include img.html img="Multi-organization-practitioner_with_parent.png" caption="Figure 4: Provider Practicing at an Organization with multiple Locations, and Organizations" %}


### Organizational Hierarchies

The Organization Resource ties Locations and Practitioners to the business entities.

**How does the organization resource interact with location resource?**

* Every Organization with a physical place where services are provided must have a location resource
* Every Location resource SHALL be associated with an Organization

The Location resource identifies the type of services available at a specific Location. The Location resource only allows a single address.

**How does a client know if it has a department organization resource vs a top-level organization?**

* The parent Organization is the Organization resource without an Organization.PartOf. A client traversing the tree can use the Organization.PartOf to find the parent.

Figure 6 gives an example of a Health System with multiple organizations. It does not cover Affiliate relationships since [additional work](future.html) is required.

{% include img.html img="Organizational_Hierarcy.png" caption="Figure 6: Example Organizational Hierarchy" %}

The FHIR STU3 includes an [example Organization hierarchy](http://build.fhir.org/organization.html#example).


### Facility Structure

FHIR supports a full location hierarchy to describe departments, rooms, beds, and other locations. Location hierarchies are important for local exchange and may be relevant for a Provider Directory. For location hierarchies, see the FHIR STU3 [example Location hierarchy](http://hl7.org/fhir/location.html#example). The finer granularity of facility structure is important for interorganizational exchange.
The Argonaut Provider Directory guide focused on interorganizational exchange and provider relationships to those organizations.
