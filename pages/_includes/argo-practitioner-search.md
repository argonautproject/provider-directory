
-----------

`GET [base]/Practitioner?identifier=[system]|[code]`

**Example:** GET [base]/Practitioner?identifier={{ site.data.fhir.path }}/sid/us-npi\|1497860456

*Support:* Mandatory to search by identifier.

*Implementation Notes:*  Search based on practitioner identifier  [(how to search by token)].


-----------

`GET [base]/Practitioner?family=[string]&given=[string]`

**Example:** GET [base]/Practitioner?family=Smith&given=John

*Support:* Mandatory to support search by Practitioner name.

*Implementation Notes:* Search based on text name [(how to search by string)].



  [(how to search by reference)]: {{ site.data.fhir.path }}/search.html#reference
  [(how to search by token)]: {{ site.data.fhir.path }}/search.html#token
 [(how to search by date)]: {{ site.data.fhir.path }}/search.html#date
 [(how to search by string)]: {{ site.data.fhir.path }}/search.html#string
