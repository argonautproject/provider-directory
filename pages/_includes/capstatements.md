## {{ page.title }}
{:.no_toc}

<!-- source pages/\_include/{{page.md_filename}}.md  file -->

<!-- TOC  the css styling for this is \pages\assets\css\project.css under 'markdown-toc'-->

* Do not remove this line (it will not be displayed)
{:toc}

<!-- end TOC -->

This section outlines conformance requirements for each of the Provider Directory actors identifying the specific profiles that need to be supported, the specific RESTful operations that need to be supported, and the search parameters that need to be supported. Note: The individual profiles identify the structural constraints, terminology bindings and invariants, however, implementers must refer to the conformance requirements for details on the RESTful operations, specific profiles and the search parameters applicable to each of the Provider Directory actors.

### Conformance requirements for an Argonaut Provider Directory Server {#server}

Source Resource: [XML](CapabilityStatement-server.xml.html)/[JSON](CapabilityStatement-server.json.html)

- FHIR Version: 3.0.0
- Supported formats: xml, json
- Published: 2017-04-30
- Published by: Argonaut

The Section describes the expected capabilities of the Provider Directory actor which is responsible for providing responses to the queries submitted by Client applications. It describes the complete list of FHIR profiles, RESTful operations, and search parameters supported by US Provider Directory Servers. Provider Directory Clients have the option of choosing from this list to access necessary data based on their local use cases and other contextual requirements.

#### Behavior

Description: The Provider Directory Server **SHALL**:

- Support the following US Provider Directory resource profiles:
   - Argonaut Endpoint
   - Argonaut Location
   - Argonaut Organization
   - Argonaut Practitioner
   - Argonaut PractitionerRole
- Return the following response classes:
   - (Status 200): successful operation
   - (Status 400): invalid parameter
   - (Status 401/4xx): unauthorized request
   - (Status 403): insufficient scope
   - (Status 404): unknown resource
   - (Status 410): deleted resource.
- Implement the RESTful behavior according to the FHIR specification.
- Support *json* resource formats for all Provider Directory interactions.
- Declare a CapabilityStatement identifying the list of profiles, operations, search parameter supported.


#### Security:

US Provider Directory Servers **SHALL**:

- Implement the security requirements documented in the [US Core IG](http://hl7.org/fhir/us/core/security.html).
- A server has ensured that every API request includes a valid Authorization token, supplied via: `Authorization: Bearer {server-specific-token-here}`
- A server has rejected any unauthorized requests by returning an `HTTP 401` Unauthorized response code.

#### Profile Interaction Summary:

- All servers **SHALL** make available the [read]({{ site.data.fhir.path }}/http.html#read) and [search]({{ site.data.fhir.path }}/http.html#search) interactions for the Profiles the server chooses to support.
- All servers **SHOULD** make available the [vread]({{ site.data.fhir.path }}/http.html#vread) and [history-instance]({{ site.data.fhir.path }}/http.html#history) interactions for the Profiles the server chooses to support.

**Summary of Provider Directory search criteria**

Specific server search capabilities are described in detail below in each of the resource sections.  When returning a PractitionerRole, a Practitioner and Endpoint **SHALL** be included. When searching on Organization or Location, a server **SHALL** support the _include parameter for the endpoint parameter. The client application must properly process a bundle when all resources are included, and must be able to retrieve them when not included.

| Resource Type | Supported Profiles | Supported Search parameters| Supported \_includes |
| ------- | -------- | -------- | -------- |
| [Endpoint](#endpoint) | Argonaut Endpoint Profile | identifier, organization, name ||
| [Location](#location) | Argonaut Location Profile | identifier, name, address | Location:endpoint |
| [Organization](#organization) | Argonaut Organization Profile | identifier, name, address | Organization:endpoint |
| [Practitioner](#practitioner) | Argonaut Practitioner Profile | identifier, name | |
| [PractitionerRole](#practitionerrole)| Argonaut PractitionerRole Profile | practitioner, specialty |PractitionerRole:practitioner, PractitionerRole:endpoint|
{:.grid}

#### Resource  Details:

##### 1. Endpoint

Supported Profiles:  [Argonaut Endpoint Profile](StructureDefinition-argo-endpoint.html)

Search Criteria:

A server **SHALL** be capable of fetching an Endpoint using:

- `GET [base]/Endpoint?identifier=[system]|[code]`
- `GET [base]/Endpoint?organization=[id]`
- `GET [base]/Endpoint?name=[string]`

| Conformance | Parameter | Type | \_include (see documentation) |
| ---|---|---|---|
| **SHALL** | identifier| token | |
| **SHALL** | name| string | |
| **SHALL** | organization| reference | |
{:.grid}

##### 2. Location
Supported Profiles:  [Argonaut Location Profile](StructureDefinition-argo-location.html)

Search Criteria:

A server **SHALL** be capable of returning a Location using:

- `GET [base]/Location?identifier=[system]|[code]{&_include=Location:endpoint}`
- `GET [base]/Location?name=[string]{&_include=Location:endpoint}`
- `GET [base]/Location?address=[string]{&_include=Location:endpoint}`

Search Parameters:

| Conformance | Parameter | Type | \_include (see documentation) |
| ---|---|---|---|
| **SHALL** | identifier| token | Location:endpoint|
| **SHALL** | name| string |Location:endpoint |
| **SHALL** | address | string |Location:endpoint |
{:.grid}

##### 3. Organization
Supported Profiles:  [Argonaut Organization Profile](StructureDefinition-argo-organization.html)

Search Criteria:

A server **SHALL** be capable of returning an Organization using:

- `GET [base]/Organization?identifier=[system]|[code]{&_include=Organization:endpoint}`
- `GET [base]/Organization?name=[string]{&_include=Organization:endpoint}`
- `GET [base]/Organization?address=[string]{&_include=Organization:endpoint}`

| Conformance | Parameter | Type | \_include (see documentation) |
| ---|---|---|---|
| **SHALL** | identifier| token | Organization:endpoint|
| **SHALL** | name| string |Organization:endpoint |
| **SHALL** | address | string |Organization:endpoint |
{:.grid}

##### 4. Practitioner
Supported Profiles:  [Argonaut Practitioner Profile](StructureDefinition-argo-practitioner.html)

Search Criteria:

A server **SHALL** be capable of returning a Practitioner using:

- `GET [base]/Practitioner?identifier=[system]|[code]`
- `GET [base]/Practitioner?family=[string]&given=[string]`
- `GET [base]/Practitioner?name=[string]`

| Conformance | Parameter | Type | \_include (see documentation) |
| ---|---|---|---|
| **SHALL** | identifier| token ||
| **SHALL** | given| string ||
| **SHALL** | family| string ||
| **SHALL** | name| string ||
{:.grid}

##### 5. PractitionerRole
Supported Profiles:  [Argonaut PractitionerRole Profile](StructureDefinition-argo-practitionerrole.html)

Search Criteria:

A server **SHALL** be capable of returning a PractitionerRole using:

- `GET [base]/PractitionerRole?practitioner.identifier=[system]|[code]{&_include=PractitionerRole:practitioner&_include=PractitionerRole:endpoint}`
- `GET [base]/PractitionerRole?practitioner.family=[string]&given=[string]{&_include=PractitionerRole:practitioner&_include=PractitionerRole:endpoint}`
- `GET [base]/PractitionerRole?specialty=[system]|[code]{&_include=PractitionerRole:practitioner&_include=PractitionerRole:endpoint}`

A server **MAY** return a PractitionerRole using:

- `GET [base]/PractitionerRole?location.address-city=[city]{&_include=PractitionerRole:practitioner&_include=PractitionerRole:endpoint}`
- `GET [base]/PractitionerRole?location.address-city=[city]&specialty=[string]{&_include=PractitionerRole:practitioner&_include=PractitionerRole:endpoint}`
- `GET [base]/PractitionerRole?location.near=[lat],[long]&near-distance=[distance]{&_include=PractitionerRole:practitioner&_include=PractitionerRole:endpoint}`

Search Parameters:

| Conformance | Parameter | Type |  \_include (see documentation) |
| ---|---|---|---|
| **SHALL** | practitioner.identifier | reference + token (chained parameter)|PractitionerRole:practitioner, PractitionerRole:endpoint|
| **SHALL** | practitioner.family | reference + string (chained parameter) |PractitionerRole:practitioner, PractitionerRole:endpoint|
| **SHALL** | specialty | token |PractitionerRole:practitioner, PractitionerRole:endpoint|
| **MAY** | location.address | reference + string (chained parameter) |PractitionerRole:practitioner, PractitionerRole:endpoint|
| **MAY** | location.near, location.distance | reference + token (chained parameter), reference + quantity (chained parameter)  |PractitionerRole:practitioner, PractitionerRole:endpoint|
{:.grid}

<br />

### Conformance requirements for the Argonaut Provider Directory Client

Source Resource: [XML](CapabilityStatement-client.xml.html)/[JSON](CapabilityStatement-client.json.html)

- FHIR Version: 3.0.0
- Supported formats: xml, json
- Published: 2017-04-30
- Published by: Argonaut

This section describes the expected capabilities of a client actor which is responsible for creating and initiating the queries for information. It is expected that this CapabilityStatement will be used in conjuction with the [Argonaut Provider Directory Server CapabilityStatement](capstatements.html#server). Together they describe the basic expectations for the capabilities of a conformant client application.

#### Behavior

The Argonaut Provider Client **SHALL** support fetching and querying of one or more Argonaut Provider profile(s), using the supported RESTful interactions and search parameters declared in the [Argonaut Provider Directory Server CapabilityStatement](capstatements.html#server)

The Argonaut Provider Client **SHOULD** Declare a CapabilityStatement identifying the list of profiles, operations, search parameter supported.

#### Security

Argonaut Clent **SHALL** implement the security requirements documented in the [US Core IG](http://hl7.org/fhir/us/core/security.html).

**Summary of Argonaut Provider search criteria**

Specific client search capabilities are described in detail below in each of the resource sections. When a Server returns a PractitionerRole, Location, or Organization, an Endpoint **MAY** be included. The client application **SHALL** properly process a bundle when all resources are included, and be able to retrieve the Endpoint resource when not included.

#### Resource  Details:

##### 1. Endpoint

Supported Profiles:  [Argonaut Endpoint Profile](StructureDefinition-argo-endpoint.html)

Search Criteria:

A Client **SHALL** be capable of fetching an Endpoint using:

- `GET [base]/Endpoint?identifier=[system]|[code]`
- `GET [base]/Endpoint?organization=[id]`
- `GET [base]/Endpoint?name=[string]`

##### 2. Location
Supported Profiles:  [Argonaut Location Profile](StructureDefinition-argo-location.html)

Search Criteria:

A client **SHALL** be capable of fetching a Location using:

- `GET [base]/Location?identifier=[system]|[code]{&_include=Location:endpoint}`
- `GET [base]/Location?name=[string]{&_include=Location:endpoint}`
- `GET [base]/Location?address=[string]{&_include=Location:endpoint}`

##### 3. Organization
Supported Profiles:  [Argonaut Organization Profile](StructureDefinition-argo-organization.html)

Search Criteria:

A client **SHALL** be capable of fetching an Organization using:

- `GET [base]/Organization?identifier=[system]|[code]{&_include=Organization:endpoint}`
- `GET [base]/Organization?name=[string]{&_include=Organization:endpoint}`
- `GET [base]/Organization?address=[string]{&_include=Organization:endpoint}`

##### 4. Practitioner
Supported Profiles:  [Argonaut Practitioner Profile](StructureDefinition-argo-practitioner.html)

Search Criteria:

A client **SHALL** be capable of fetching a Practitioner using:

- `GET [base]/Practitioner?identifier=[system]|[code]`
- `GET [base]/Practitioner?family=[string]&given=[string]`
- `GET [base]/Practitioner?name=[string]`

##### 5. PractitionerRole
Supported Profiles:  [Argonaut PractitionerRole Profile](StructureDefinition-argo-practitionerrole.html)

Search Criteria:

A client **SHALL** be capable of fetching a PractitionerRole using:

- `GET [base]/PractitionerRole?practitioner.identifier=[system]|[code]{&_include=PractitionerRole:practitioner&_include=PractitionerRole:endpoint}`
- `GET [base]/PractitionerRole?practitioner.family=[string]&given=[string]{&_include=PractitionerRole:practitioner&_include=PractitionerRole:endpoint}`
- `GET [base]/PractitionerRole?specialty=[system]|[code]{&_include=PractitionerRole:practitioner&_include=PractitionerRole:endpoint}`

<br />
