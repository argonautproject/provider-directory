This profile sets minimum expectations for the [Location] resource for recording, searching for and fetching a Location associated with a provider or organization. It identifies which core elements, extensions, vocabularies and value sets **SHALL** be present in the resource when using this profile.


##### Mandatory Data Elements and Terminology


The following data-elements are mandatory (i.e data MUST be present). These are presented below in a simple human-readable explanation.  Profile specific guidance and examples are provided as well.  The [**Formal Profile Definition**](#profile) below provides the  formal summary, definitions, and  terminology requirements.  

**Each Location must have:**

Each Location must have:

1. A status of the Location
1. A name
1. A list of contact information
1. A managing Organization

Each Location *SHOULD* have:

1. A Location type
1. A  Location identifier

**Profile specific implementation guidance:**

 * A server *SHALL* support the [_include](http://build.fhir.org/search.html#include) parameter when retrieving a Location resource.

[Location]:  http://build.fhir.org/location.html

##### Examples

- [Location-1](Location-example-location-1.html)
- [Location-2-with-Endpoint](Location-example-location-2.html)
- [Location-3-minimum](Location-example-location-3.html)

