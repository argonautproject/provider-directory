
-----------

`GET [base]/Location?identifier=[system]|[code]`

**Example:** GET [base]/Location?identifier=http://hospital.smarthealthit.org/Location|123571

*Support:* Mandatory to search by identifier. 

*Implementation Notes:*  Search based on Location identifier  [(how to search by token)].

-----------

`GET [base]/Location?name=[string]`

**Example:** GET [base]/Location?name=Health

*Support:* Mandatory to suppport search by Location name.

*Implementation Notes:* Search based on text name [(how to search by string)].

-----

`GET [base]/Location?address=[string]`

**Example:** GET [base]/Location?address=Arbor

**Example:** GET [base]/Location?address-postalcode=48104

*Support:*  Mandatory to suppport search by address.

*Implementation Notes:* Search based on text address [(how to search by string)].

**SHOULD** support the following search parameters:

- address-city
- address-state
- address-postalcode


-----


  [(how to search by reference)]: http://build.fhir.org/search.html#reference
  [(how to search by token)]: http://build.fhir.org/search.html#token
 [(how to search by date)]: http://build.fhir.org/search.html#date
 [(how to search by string)]: http://build.fhir.org/search.html#string
