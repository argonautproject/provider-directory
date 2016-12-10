



-------------------------

**Clients**

-  A client has connected to a server and fetched a Endpoint by identifier using `GET [base]/Endpoint?identifier=[system]|[code]`
- A client has connected to a server and fetched a Endpoint by organization using `GET [base]/Endpoint?organization=[id]`
- A client has connected to a server and fetched a Endpoint by name using 'GET [base]/Endpoint?name=[string]'

**Servers**

- A server is capable of returning a Endpoint by identifier using `GET [base]/Endpoint?identifier=[system]|[code]`
- A server is capable of returning a Endpoint  by organization using `GET [base]/Endpoint?organization=[id]`
- A server is capable of returning a Endpoint by name using 'GET [base]/Endpoint?name=[string]'

-   A server has ensured that every API request includes a valid Authorization token, supplied via:Authorization: Bearer {server-specific-token-here}
-   A server has rejected any unauthorized requests by returning an HTTP 401 Unauthorized response code.

-----------

**GET [base]/Endpoint?identifier=[system]|[code]**

*Support:* Mandatory

*Implementation Notes:*  Search based on Endpoint identifier  [(how to search by token)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

[GET http://fhir2.healthintersections.com.au/open/Location?identifier=urn:ietf:rfc:3986%7C2.16.840.1.113883.19.5](http://fhir2.healthintersections.com.au/open/Location?identifier=urn:ietf:rfc:3986%7C2.16.840.1.113883.19.5)

-----------

**GET [base]/Endpoint?name=[string]**

*Support:* Mandatory

*Implementation Notes:* Search based on text name [(how to search by string)].
*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

[GET https://fhir-open-api-dstu2.smarthealthit.org/Location?name=Health](https://fhir-open-api-dstu2.smarthealthit.org/Location?name=Health)

-----------


**GET [base]/Endpoint?organization=[id]**

*Support:* Mandatory

*Implementation Notes:* Search based on organization  [(how to search by reference)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

TBD


  [(how to search by reference)]: http://hl7.org/fhir/search.html#reference
  [(how to search by token)]: http://hl7.org/fhir/search.html#token
 [(how to search by date)]: http://hl7.org/fhir/search.html#date
 [(how to search by string)]: http://hl7.org/fhir/search.html#string
