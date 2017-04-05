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

This IG describes the basic resources and required elements to form a robust Provider Directory. During the development of the guide, the team discusses the relationpships between resoruces and draft a few diagrams. First, figure 1 is a basic diagram of single provider practice.

{% include img.html img="Single-provider-practice.png" caption="Figure 1: Single Provider Practice" %}

In Figure 2, the diagram represent a single practitioner working at multiple locations within a single organization.

{% include img.html img="Multi-organization-practitioner.png" caption="Figure 2: Provider Practicing at Multiple Organizations" %}


Increasing in complexity, is Figure 3, which is a group of providers practicing at multiple locations.

{% include img.html img="Multi-Location-provider-practice.png" caption="Figure 3: Providers Practicing at Multiple Locations" %}

This could also have a single parent organization over the two sub-organizations.

{% include img.html img="Multi-organization-practitioner_with_parent.png" caption="Figure 4: Provider Practicing at an Organziation with multiple Locations, and Organizations" %}




### Facility Structure

From STU3, [Example Organization Hierarchy](http://hl7.org/fhir/organization.html#example) and [Example Location Hierarchy](http://hl7.org/fhir/location.html#example).