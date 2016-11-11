



-------------------------

**Clients**

-  A client has connected to a server and fetched an organization by identifier using `GET [base]/Organization?identifier=[system]|[code]`
- A client has connected to a server and fetched an organization by name using`GET [base]/Organization?name=[string]`
- A client has connected to a server and fetched an organization by address using `GET [base]/Organization?address=[string]`


**Servers**

- A server is capable of returning an organization by identifier using `GET [base]/Organization?identifier=[system]|[code]`
- A server is capable of returning an organization by name using `GET [base]/Organization?name=[string]`
- A server is capable of returning an organization by address using `GET [base]/Organization?address=[string]`


-   A server has ensured that every API request includes a valid Authorization token, supplied via:Authorization: Bearer {server-specific-token-here}
-   A server has rejected any unauthorized requests by returning an HTTP 401 Unauthorized response code.

-----------

**GET [base]/Organization?identifier=[system]|[code]**

*Support:* Mandatory

*Implementation Notes:*  Search based on Organization identifier  [(how to search by token)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request
-   (Status 403): insufficient scope

*Example:*

[GET https://fhir-open-api-dstu2.smarthealthit.org/Organization?name=Health](https://fhir-open-api-dstu2.smarthealthit.org/Organization?name=Health)

-----------


**GET [base]/Organization?name=[string]**

*Support:* Mandatory

*Implementation Notes:* Search based on text name [(how to search by string)].

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request
-   (Status 403): insufficient scope

*Example:*

[GET https://fhir-open-api-dstu2.smarthealthit.org/Organization?name=Health](https://fhir-open-api-dstu2.smarthealthit.org/Organization?name=Health)

-----------


**GET [base]/Organization?address=[string]**

*Support:* Mandatory

*Implementation Notes:* Search based on text address [(how to search by string)].

SHOULD also support the search parameters:

- address-city
- address-state
- address-postalcode

*Response Class:*

-   (Status 200): successful operation
-   (Status 400): invalid parameter
-   (Status 401/4xx): unauthorized request
-   (Status 403): insufficient scope

*Example:*

[GET https://fhir-open-api-dstu2.smarthealthit.org/Organization?address=Arbor](https://fhir-open-api-dstu2.smarthealthit.org/Organization?address=Arbor)

[GET https://fhir-open-api-dstu2.smarthealthit.org/Organization?address-postalcode=48104](https://fhir-open-api-dstu2.smarthealthit.org/Organization?address-postalcode=48104)


  [(how to search by reference)]: http://hl7.org/fhir/DSTU2/search.html#reference
  [(how to search by token)]: http://hl7.org/fhir/DSTU2/search.html#token
 [(how to search by date)]: http://hl7.org/fhir/DSTU2/search.html#date
 [(how to search by string)]: http://hl7.org/fhir/DSTU2/search.html#string
