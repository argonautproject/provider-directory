
-------------------------

**Clients**

-  A client has connected to a server and fetched a practitioner by identifier using `GET [base]/Practitioner?identifier=[system]|[code]`
- A client has connected to a server and fetched a practitioner by name using `GET [base]/Practitioner?family=[string]&given=[string]`


**Servers**

- A server is capable of returning a practitioner by identifier using `GET [base]/Practitioner?identifier=[system]|[code]`
- A server is capable of returning a practitioner by name using `GET [base]/Practitioner?family=[string]&given=[string]`


-   A server has ensured that every API request includes a valid Authorization token, supplied via:Authorization: Bearer {server-specific-token-here}
-   A server has rejected any unauthorized requests by returning an HTTP 401 Unauthorized response code.

-----------

**GET [base]/Practitioner?identifier=[system]|[code]**

*Support:* Mandatory

*Implementation Notes:*  Search based on practitioner identifier  [(how to search by token)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

[GET https://fhir-open-api-dstu2.smarthealthit.org/Practitioner?identifier=http://build.fhir.org/sid/us-npi%7C1497860456](https://fhir-open-api-dstu2.smarthealthit.org/Practitioner?identifier=http://build.fhir.org/sid/us-npi%7C1497860456)

-----------


**GET [base]/Practitioner?family=[string]&given=[string]**

*Support:* Mandatory

*Implementation Notes:* Search based on text name [(how to search by string)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

[GET https://fhir-open-api-dstu2.smarthealthit.org/Practitioner?family=Smith&given=John](https://fhir-open-api-dstu2.smarthealthit.org/Practitioner?family=Smith&given=John)



  [(how to search by reference)]: http://build.fhir.org/search.html#reference
  [(how to search by token)]: http://build.fhir.org/search.html#token
 [(how to search by date)]: http://build.fhir.org/search.html#date
 [(how to search by string)]: http://build.fhir.org/search.html#string
