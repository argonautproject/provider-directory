
-----------

`GET [base]/Organization?identifier=[system]|[code]`

**Example:** GET [base]/Organization?identifier=http://hospital.smarthealthit.org/Organization\|103270514

*Support:* Mandatory to search by identifier.

*Implementation Notes:*  Search based on Organization identifier  [(how to search by token)].

-----------

`GET [base]/Organization?name=[string]`

**Example:** GET [base]/Organization?name=Health system

*Support:* Mandatory to support search by Organization name.

*Implementation Notes:* Search based on text name [(how to search by string)].

-----------

`GET [base]/Organization?address=[string]`

**Example:** GET [base]/Organization?address=Arbor

**Example:** GET [base]/ORganization?address-postalcode=48104

*Support:*  Mandatory to support search by address.

*Implementation Notes:* Search based on text address [(how to search by string)].

**SHOULD** support the following search parameters:

- address-city
- address-state
- address-postalcode



  [(how to search by reference)]: http://hl7.org/fhir/search.html#reference
  [(how to search by token)]: http://hl7.org/fhir/search.html#token
 [(how to search by date)]: http://hl7.org/fhir/search.html#date
 [(how to search by string)]: http://hl7.org/fhir/search.html#string
