## {{ page.title }}
{:.no_toc}

source pages/\_include/{{page.md_filename}}.md  file

This section outlines conformance requirements for each of the Provider Directory actors identifying the specific profiles that need to be supported, the specific RESTful operations that need to be supported, and the search parameters that need to be supported. Note: The individual profiles identify the structural constraints, terminology bindings and invariants, however, implementers must refer to the conformance requirements for details on the RESTful operations, specific profiles and the search parameters applicable to each of the Provider Directory actors.

---

<!-- TOC  the css styling for this is \pages\assets\css\project.css under 'markdown-toc'-->

* Do not remove this line (it will not be displayed)
{:toc}

<!-- end TOC -->


### Conformance requirements for an Argonaut Provider Directory Server

Source Resource: [XML](CapabilityStatement-server.xml.html)/[JSON](CapabilityStatement-server.json.html)

- FHIR Version: 3.0.0
- Supported formats: xml, json
- Published: 2017-04-30
- Published by: Argonaut

The Section describes the expected capabilities of the Provider Directory actor which is responsible for providing responses to the queries submitted by Client applications. It describes the complete list of FHIR profiles, RESTful operations, and search parameters supported by US Provider Directory Servers. Provider Directory Clients have the option of choosing from this list to access necessary data based on their local use cases and other contextual requirements.

#### Behavior

Description: The Provider Directory Server **SHALL**:

- Support the following US Provider Directory resource profiles:
   - Argonaut EndPoint
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

Specific server search capabilities are described in detail below in each of the resource sections.  When returning a PractitionerRole, a Practitioner and Endpoint SHALL be included. A server SHALL support the _include parameter when searching on Organization or Location. The client application must handle when all resources are included, and must be able to retrieve when not included. 

| Resource Type | Supported Profiles | Supported Searches | Supported \_includes |
| ------- | -------- | -------- | -------- |
| [Endpoint](#endpoint) | Argonaut Endpoint Profile | identifier, organization, name ||
| [Location](#location) | Argonaut Location Profile | identifier, name, address | Location:endpoint |
| [Organization](#organization) | Argonaut Organization Profile | identifier, name, address | Organization:endpoint |
| [Practitioner](#practitioner) | Argonaut Practitioner Profile | identifier, name | |
| [PractitionerRole](#practitionerrole)| Argonaut PractitionerRole Profile | practitioner, specialty ||
{:.grid}

#### Resource  Details:

##### 1. Endpoint

Supported Profiles:  [Argonaut Endpoint Profile](todo.html)

Search Criteria:

A server **SHALL** be capable of fetching an Endpoing using:

- `GET [base]/Endpoint?identifier=[system]|[code]`
- `GET [base]/Endpoint?organization=[id]`
- `GET [base]/Endpoint?name=[string]`

| Conformance | Parameter | Type | \_include (see documentation) | Modifiers |
| ---|---|---|---|--- |
| **SHALL** | Organization + identifier | reference | | |
{:.grid}

##### 2. Location
Supported Profiles:  [Argonaut Location Profile](todo.html)

Search Criteria:

A server **SHALL** be capable of fetching a Location using:

- `GET [base]/Location?identifier=[system]|[code]`
- `GET [base]/Location?name=[string]`
- `GET [base]/Location?address=[string]`

Search Parameters:

| Conformance | Parameter | Type | \_include (see documentation) | Modifiers |
| ---|---|---|---|--- |
| **SHALL** | | reference |  Location:endoint | |
{:.grid}

##### 3. Organization
Supported Profiles:  [Argonaut Organization Profile](todo.html)

Search Criteria:

A server **SHALL** be capable of returning an Organization using:

- `GET [base]/Organization?identifier=[system]|[code]`
- `GET [base]/Organization?name=[string]`
- `GET [base]/Organization?address=[string]`

| Conformance | Parameter | Type | \_include (see documentation) | Modifiers |
| ---|---|---|---|--- |
| **SHALL** | | reference |  Organization:endoint | |
{:.grid}

##### 4. Practitioner
Supported Profiles:  [Argonaut Practitioner Profile](todo.html)

Search Criteria:

A server **SHALL** be capable of returning a Practitioner using:

- `GET [base]/Practitioner?identifier=[system]|[code]`
- `GET [base]/Practitioner?family=[string]&given=[string]`

##### 5. PractitionerRole
Supported Profiles:  [Argonaut PractitionerRole Profile](todo.html)

Search Criteria:

A server **SHALL** be capable of returning a PractitionerRole using:

- `GET [base]/PractitionerRole?practitioner.identifier=[system]|[code]`
- `GET [base]/PractitionerRole?practitioner.family=[string]&given=[string]`
- `GET [base]/PractitionerRole?specialty=[system]|[code]`

A server **MAY** return a PractitionerRole using:

- `GET [base]/Practitioner?location.address-city=[city]` 
- `GET [base]/Practitioner?location.address-city=[city]&specialty=[string]` 
- `GET [base]/Practitioner?location.near=-72.519854,42.373222&near-distance=2m`

Search Parameters:

| Conformance | Parameter | Type |  \_include (see documentation) | Modifiers |
| ---|---|---|---|--- |
| **SHALL** | practitioner + identifier | reference + token | 
| **SHALL** | practitioner + family | reference + token | 
| **SHALL** | specialty | token |  |
{:.grid}

<br />

### Conformance requirements for the Argonaut Provider Directory Client - START HERE TOMORROW AFTER QA ABOVE

Source Resource: [XML](CapabilityStatement-client.xml.html)/[JSON](CapabilityStatement-client.json.html)

- FHIR Version: 3.0.0
- Supported formats: xml, json
- Published: 2017-04-30
- Published by: Argonaut

This section describes the expected capabilities of a client actor which is responsible for creating and initiating the queries for information about an individual patient.It is expected that this CapabilityStatement will be used in conjuction with the [US Core CapabilityStatement](todo.html). Together they describe the basic expectations for the capabilities of a conformant client application. The complete list of actual profiles and dependencies on other profiles outside the FHIR specification RESTful interactions which includes the search and read operations that **MAY** be supported by the client

#### Behavior

The US Meds Clent **SHALL** support fetching and querying of one or more US Meds profile(s), using the supported RESTful interactions and search parameters declared in the [US Meds Server CapabilityStatement](#conformance-requirements-for-the-us-meds-server)

The US Meds Clent **SHOULD** Declare a CapabilityStatement identifying the list of profiles, operations, search parameter supported.

#### Security

US Core Servers **SHALL** implement the security requirements documented in the [US-Core IG](todo.html).

**Summary of US Meds search criteria**

Specific client search capabilities are described in detail below in each of the resource sections.  The MedicationAdministration, MedicationDispense, MedicationStatement and MedicationRequest resources can represent a medication using either a code or refer to the Medication resource.  When referencing a Medication resource, the resource may be contained or an external resource. The server application can choose any one way or more than one method, but *if* the an external reference to Medication is used, the server **SHALL** support the [`_include`](todo.html) parameter for searching this element. The client application **SHALL** support all above methods without causing the application to fail.

#### Resource  Details:

##### 1. Medication

Supported Profiles:  [US Core Medication Profile](todo.html)

##### 2. MedicationAdministration
Supported Profiles:  [US Core MedicationAdministration Profile](todo.html)

Search Criteria:

A client **SHALL** be capable of fetching a patient's administered medications using:

- `GET /MedicationAdministration?patient=[id]`
- `GET /MedicationAdministration?patient=[id]&_include=MedicationAdministration:medication`


##### 3. MedicationDispense
Supported Profiles:  [US Core MedicationDispense Profile](todo.html)

Search Criteria:


A client **SHALL** be capable of fetching a patient's dispensed medications using:

- `GET /MedicationDispense?patient=[id]`
- `GET /MedicationDispense?patient=[id]&_include=MedicationDispense:medication`

##### 4. MedicationRequest
Supported Profiles:  [US Core MedicationRequest Profile](todo.html)

Search Criteria:


A client **SHALL** be capable of fetching all patient’s active medications orders using:

- `GET /MedicationRequest?patient=[id]&status=active`
- `GET /MedicationRequest?patient=[id]&status=active&_include=MedicationRequest:medication`

##### 5. MedicationStatement
Supported Profiles:  [US Core MedicationStatement Profile](todo.html)

Search Criteria:

A client **SHALL** be capable of fetching all medications for a patient using:

- `GET /MedicationStatement?patient=[id]`
- `GET /MedicationStatement?patient=[id]&_include=MedicationStatement:medication`

A client **SHALL** be capable of fetching all active medications for a patient using:

- `GET /MedicationStatement?patient=[id]&status=active`
- `GET /MedicationStatement?patient=[id]&status=active&_include=MedicationStatement:medication`

A client **SHALL** be capable of fetching all medications for a patient for an encounter using:

- `GET /MedicationStatement?patient=[id]&context=[id]`
- `GET /MedicationStatement?patient=[id]&context=[id]&_include=MedicationStatement:medication`

<br />
