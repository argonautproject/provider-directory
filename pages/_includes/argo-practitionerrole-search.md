



-------------------------

**Clients**

-  A client has connected to a server and fetched a PractionerRole by identifier using `GET [base]/PractionerRole?identifier=[system]|[code]`
- A client has connected to a server and fetched a PractionerRole by name using `GET [base]/PractionerRole?family=[string]&given=[string]`
- A client has connected to a server and fetched a PractitionerRole by specialty using 'GET [base]/PractitionerRole?specialty=[system]|[code]'

**Servers**

- A server is capable of returning a PractionerRole by identifier using `GET [base]/PractionerRole?identifier=[system]|[code]`
- A server is capable of returning a PractionerRole by name using `GET [base]/PractionerRole?family=[string]&given=[string]`
- A server is capable of returning a PractitionerRole by specialty using GET [base]/PractitionerRole?specialty=[system]|[code]

-   A server has ensured that every API request includes a valid Authorization token, supplied via:Authorization: Bearer {server-specific-token-here}
-   A server has rejected any unauthorized requests by returning an HTTP 401 Unauthorized response code.

-----------

**GET [base]/PractionerRole?identifier=[system]|[code]**

*Support:* Mandatory

*Implementation Notes:*  Search based on PractionerRole identifier  [(how to search by token)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

[GET https://fhir-open-api-dstu2.smarthealthit.org/PractionerRole?identifier=http://hl7.org/fhir/sid/us-npi%7C1497860456](https://fhir-open-api-dstu2.smarthealthit.org/PractionerRole?identifier=http://hl7.org/fhir/sid/us-npi%7C1497860456)

-----------


**GET [base]/PractitionerRole?practitioner.identifier=[system]|[code]**

*Support:* Mandatory

*Implementation Notes:* Search based on Practitioner identifier (NPI) [(how to search by token)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

[GET  http://fhir3.healthintersections.com.au/open/PractitionerRole?practitioner.identifier=http://hl7.org/fhir/sid/us-ssn%7C999999999](http://fhir3.healthintersections.com.au/open/PractitionerRole?practitioner.identifier=http://hl7.org/fhir/sid/us-ssn%7C999999999)



-----------


**GET [base]/PractitionerRole?practitioner.family=[string]&given=[string]**

*Support:* Mandatory

*Implementation Notes:* Search based on text name [(how to search by string)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

[GET  http://fhir3.healthintersections.com.au/open/PractitionerRole?practitioner.family=verify&given=v](http://fhir3.healthintersections.com.au/open/PractitionerRole?practitioner.family=verify&given=v)

[GET http://fhir3.healthintersections.com.au/open/PractitionerRole?practitioner.family=verify&given=v&_include=PractitionerRole:practitioner](http://fhir3.healthintersections.com.au/open/PractitionerRole?practitioner.family=verify&given=v&_include=PractitionerRole:practitioner)


-----------


**GET [base]/PractitionerRole?specialty=[system]|[code]]**

*Support:* Mandatory

*Implementation Notes:*  Search based on specialty [(how to search by token)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

[GET  http://fhir3.healthintersections.com.au/open/PractitionerRole?specialty=http://hl7.org/fhir/practitioner-specialty%7Ccardio](http://fhir3.healthintersections.com.au/open/PractitionerRole?specialty=http://hl7.org/fhir/practitioner-specialty%7Ccardio)

[Get http://fhir3.healthintersections.com.au/open/PractitionerRole?specialty:text=cardio&_include=PractitionerRole:practitioner](http://fhir3.healthintersections.com.au/open/PractitionerRole?specialty:text=cardio&_include=PractitionerRole:practitioner)

-----------
**Searches under development**

   GET [base]/Practitioner?location.address-city=[city]
   GET [base]/Practitioner?location.address-city=[city]&specialty=[string]
   GET [base]/Practitioner?location.near=-72.519854,42.373222&near-distance=2m

*Support:* Mandatory

*Implementation Notes:*  Search based on location [(how to search by reference)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

TBD


  [(how to search by reference)]: http://hl7.org/fhir/DSTU2/search.html#reference
  [(how to search by token)]: http://hl7.org/fhir/DSTU2/search.html#token
 [(how to search by date)]: http://hl7.org/fhir/DSTU2/search.html#date
 [(how to search by string)]: http://hl7.org/fhir/DSTU2/search.html#string
