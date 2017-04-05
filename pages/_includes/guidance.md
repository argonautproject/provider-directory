## {{ page.title }}
{:.no_toc}


<!-- TOC  the css styling for this is \pages\assets\css\project.css under 'markdown-toc'-->

* Do not remove this line (it will not be displayed)
{:toc}

<!-- end TOC -->

This section outlines the definitions and interpretations and specific guidance for the Argonaut Provider Directory Guide.  The conformance verbs used are defined in [FHIR Conformance Rules](capstatements.html).


source pages/\_include/{{page.md_filename}}.md  file

### Background on the PD Resource Relationships

#### Relationships between Practitioner, Organization, Location, and Endpoints
{:.no_toc}

This IG describes the basic resources and required elements to form a robust Provider Directory. During the development of the guide, the team discussed the relationships between resources and drafted serveral diagrams. First, figure 1 is a basic diagram of single provider practice.

{% include img.html img="Single-provider-practice.png" caption="Figure 1: Single Provider Practice" %}

In Figure 2, the diagram represent a single practitioner working at multiple locations within a single organization.

{% include img.html img="Multi-organization-practitioner.png" caption="Figure 2: Provider Practicing at Multiple Organizations" %}


Increasing in complexity, is Figure 3, which is a group of providers practicing at multiple locations.

{% include img.html img="Multi-Location-provider-practice.png" caption="Figure 3: Providers Practicing at Multiple Locations" %}

This could also have a single parent organization over the two sub-organizations.

{% include img.html img="Multi-organization-practitioner_with_parent.png" caption="Figure 4: Provider Practicing at an Organziation with multiple Locations, and Organizations" %}


### Organizational Hierarchies

The Organization Resource ties Locations and Practioners to the business entities.

**How does the organization resource interact with location resource?**

* Every Organization with a physical place where services are provided must have a location resource
* Every Location resource SHALL be associated with an Organization

The Location resource identifies the type of services available at a specific Location. The Location resource only allows a single address.

**How does a client know if it has a department organizatoin resource vs a top-level organization?**

* The parent Organzation is the Organization resource without an Organization.PartOf. A system traversing the tree can use the Organization.PartOf to find the parent. 

Figure 6 gives an example of a Health System wit multiple organizations. It does not cover Affliate relationships since [additional work](future.html) is required. 

{% include img.html img="Organizational_Hierarcy.png" caption="Figure 6: Example Organizational Hierarchy" %}

The FHIR STU3 includes an [example Organization Hierarchy](http://build.fhir.org/organization.html#example).


### Facility Structure

FHIR supports a full location hierarchy to describe departments, rooms, beds, and other locations. Location hierarchies are important for local exchange and may be relevant for a Provider Directory. For location hierarchies, see the FHIR STU3 [example Location hierarchy](http://hl7.org/fhir/location.html#example). The finer granularity of facility structure is important for interorganizational exchange.
The Argonaut PD focused on interorganizational exchange and providers relationships to those organizations. 