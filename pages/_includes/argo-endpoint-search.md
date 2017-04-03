
-----------

`GET [base]/Endpoint?identifier=[system]|[code]`

**Example:** GET [base]/Endpoint?identifier=http://hospital.smarthealthit.org/EndPoints|103270514

*Support:* Mandatory to search by identifier. 

*Implementation Notes:*  Search based on Endpoint identifier  [(how to search by token)].

-----------

`GET [base]/Endpoint?organization=[id]`

**Example:** GET [base]/Endpoint?organization=2354

*Support:* Mandatory to suppport search by organization.

*Implementation Notes:* Search based on organization  [(how to search by reference)].

-----------

`GET [base]/Endpoint?name=[string]`

**Example:** GET [base]/Endpoint?name=good health hospital

*Support:* Mandatory to suppport search by EndPoint name.

*Implementation Notes:* Search based on name [(how to search by string)].



  [(how to search by reference)]: http://hl7.org/fhir/search.html#reference
  [(how to search by token)]: http://hl7.org/fhir/search.html#token
 [(how to search by date)]: http://hl7.org/fhir/search.html#date
 [(how to search by string)]: http://hl7.org/fhir/search.html#string
