
-------------------------

**Clients**

-  A client has connected to a server and fetched a location by name using `GET [base]/Location?name=[string]`
- A client has connected to a server and fetched a location by adress using `GET [base]/Location?address=[string]`


**Servers**

- A server has connected to a server and fetched a location by name using `GET [base]/Location?name=[string]`
- A server has connected to a server and fetched a location by adress using `GET [base]/Location?address=[string]`

-   A server has ensured that every API request includes a valid Authorization token, supplied via:Authorization: Bearer {server-specific-token-here}
-   A server has rejected any unauthorized requests by returning an HTTP 401 Unauthorized response code.

-----------

<!--
**GET [base]/Location?identifier=[system]|[code]**

*Support:* Mandatory

*Implementation Notes:*  Search based on location identifier  [(how to search by token)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request


*Example:*

[GET https://fhir-open-api-dstu2.smarthealthit.org/Location?identifier=http://build.fhir.org/sid/us-npi%7C1497860456](https://fhir-open-api-dstu2.smarthealthit.org/Location?identifier=http://build.fhir.org/sid/us-npi%7C1497860456)

-----------
-->

**GET [base]/Location?name=[string]**

*Support:* Mandatory

*Implementation Notes:* Search based on text name [(how to search by string)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request
-   (Status 403): insufficient scope

*Example:*

[GET https://fhir-open-api-dstu2.smarthealthit.org/Location?name=Health](https://fhir-open-api-dstu2.smarthealthit.org/Location?name=Health)

-----


**GET [base]/Location?address=[string]**

*Support:* Mandatory

*Implementation Notes:* Search based on text address [(how to search by string)].

SHOULD also support the following search parameters:

- address-city
- address-state
- address-postalcode

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request
-   (Status 403): insufficient scope


*Example:*

[GET https://fhir-open-api-dstu2.smarthealthit.org/Location?address=Arbor](https://fhir-open-api-dstu2.smarthealthit.org/Location?address=Arbor)
[GET https://fhir-open-api-dstu2.smarthealthit.org/Location?address-postalcode=48104](https://fhir-open-api-dstu2.smarthealthit.org/Location?address-postalcode=48104)


-----


  [(how to search by reference)]: http://build.fhir.org/search.html#reference
  [(how to search by token)]: http://build.fhir.org/search.html#token
 [(how to search by date)]: http://build.fhir.org/search.html#date
 [(how to search by string)]: http://build.fhir.org/search.html#string
