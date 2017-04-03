
-----------

`GET [base]/Practitioner?identifier=[system]|[code]`

**Example:** GET [base]/Practitioner?identifier=http://build.fhir.org/sid/us-npi%7C1497860456

*Support:* Mandatory to search by identifier. 

*Implementation Notes:*  Search based on practitioner identifier  [(how to search by token)].


-----------

`GET [base]/Practitioner?family=[string]&given=[string]`

**Example:** GET [base]/Practitioner?family=Smith&given=John

*Support:* Mandatory to suppport search by Practitioner name.

*Implementation Notes:* Search based on text name [(how to search by string)].



  [(how to search by reference)]: http://build.fhir.org/search.html#reference
  [(how to search by token)]: http://build.fhir.org/search.html#token
 [(how to search by date)]: http://build.fhir.org/search.html#date
 [(how to search by string)]: http://build.fhir.org/search.html#string
