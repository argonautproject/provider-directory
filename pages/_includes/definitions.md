## Definitions
-----------

#### Extensible binding for CodeableConcept Datatype

Extensible binding to a value set definition for this IG means that if the data type is CodeableConcept, then one of the coding values SHALL be from the specified value set if a code applies, but if no suitable code exists in the value set, alternate code(s) may be provided in its place. **If only text available, then just text may be used.**

#### Required binding for Code and CodeableConcept Datatype

Required binding to a value set definition for this IG means that one of the codes from the specified value set SHALL be used. For CodeableConcept you may have additional codings elements as translations as is discussed below. If only text is available or the local (proprietary, system) cannot be mapped to one of the required codes the The [core specification] provides guidance which we have summarized:

1.  Send the resource with coded element element empty
2.  Use the [DataAbsentReason Extension] in the data type
3.  Use the code ‘unsupported’ - The source system wasn't capable of supporting this element.

Note that is will still be ambiguous when using a status based queries

Example: AllergyIntolerance resource with a status that is text only or cannot be mapped to the status value set.


    \{
       "resourceType”:“AllergyIntolerance”,
       ...
       “status”:{
        “url” : “[http://hl7.org/fhir/StructureDefinition/data-absent-reason]”,
       “valueCode” : “unsupported”
        ...
      },
     }


#### Using multiple codes with CodeableConcept Datatype

Atlernate codes may be provided in addition to the standards codes defined in required or extensible value sets. The alternate codes are called “translations”. These translations may be equivalent to or narrower in meaning to the standard concept code.

Example of multiple translation for Body Weight concept code.


    "code": {
        "coding": [
         {
            "system": "http://loinc.org",  //NOTE:this is the standard concept defined in the value set//
            "code": "29463-7",
            "display": "Body Weight"
          },
    //NOTE:this is a translation to a more specific concept
         {
            "system": "http://loinc.org",
            "code": "3141-9",
            "display": "Body Weight Measured"
          },
    //NOTE:this is a translation to a different code system (Snomed CT)
         {
            "system": "http://snomed.info/sct",
            "code":  “364589006”,
            "display": "Body Weight"
          }
    //NOTE:this is a translation to a locally defined code
         {
            "system": "http://AcmeHealthCare.org",
            "code":  “BWT”,
            "display": "Body Weight"
          }
        ],
        "text": "weight"
      },

Example of translation of NDC vaccine code to CVX code.




    "vaccineCode" : {
        "coding" : [
          {
            "system" : "http://hl7.org/fhir/sid/cvx",
            "code" : "158",
            "display" : "influenza, injectable, quadrivalent"
          },
          {
            "system" : "http://hl7.org/fhir/sid/ndc",
            "code" : "49281-0623-78",
            "display" : "FLUZONE QUADRIVALENT"
          }
        ]
      },

#### Read(Fetch) resource notation:

The interactions on IG page are defined like this:

 **`GET [base]/[Resource-type]/[id] {parameters}`**

-   GET is the HTTP verb used for fetching a resource
-   Content surrounded by \[\] is mandatory, and will be replaced by the string literal identified.
    -   base: The Service Root URL (e.g. “<https://fhir-open-api-dstu2.smarthealthit.org>”)
    -   Resource-type: The name of a resource type (e.g. “Patient”)
    -   id: The Logical Id of a resource(e.g. “24342”)
-   Content surrounded by {} is optional
    -   parameters: URL parameters as defined for the particular interaction (e.g."?\_format=xml"}

For more information see the [FHIR RESTful API]

#### Search Syntax

In the simplest case, a search is executed by performing a GET operation in the RESTful framework:

**GET [base]/[Resource-type]?name=value&...**

For this RESTful search (see definition in RESTful API), the parameters are a series of name=\[value\] pairs encoded in the URL. The search parameter names are defined for each resource. For example the Observation resource the name “code” for search on the LOINC code. See [Searching] for more information about searching in REST, messaging, and services.

#### Syntax for searches limited by patient

There are three ways to search for resources associated with a specific patient depending on the context and implementation. These three searches result in the same outcome.:

1. An explicitly defined patient that controls which set of resources are being searched by resource type:

**GET [base]/[Resource-type]?patient=24342{&otherparameters}**

Note that all the search interactions in this IG are published using the above syntax.

However there are several variations to this syntax: (see [Issue \#39])

-   GET \[base\]/\[Resource-type\]?Subject=\[id\]{&other parameters}
-   GET \[base\]/\[Resource-type\]?Subject=Patient/\[id\]{&other parameters}
-   GET \[base\]/\[Resource-type\]?Subject.\_id=\[id\]{&other parameters}
-   GET \[base\]/\[Resource-type\]?subject:Patient=\[id\]{&other parameters}
-   GET \[base\]/\[Resource-type\]?subject:Patient=Patient/\[id\]{&other parameters}
-   GET \[base\]/\[Resource-type\]?subject:Patient=<https://%5Burl%5D/Patient/id>{&other parameters}
-   GET \[base\]/\[Resource-type\]?subject:Patient.\_id=\[id\]{&other parameters}
-   GET \[base\]/\[Resource-type\]?patient:Patient=<https://%5Burl%5D/Patient/id>{&other parameters}

2. if the patient is implicit in the context (e.g. UC-1 above or using SMART), then this search applies:

**GET [base]/[Resource-type]?other-parameters**

NOTE:

-   Patient [compartment] based search with a specified resource type in that compartment is not suported for this IG.

<!-- -->

-   In addition, Argonaut servers will not resolve full URLs that are external to their environment.

#### Guidance on limiting the number of search results

In order to manage the number of search results returned, the server may choose to return the results in a series of pages. The search result set contains the URLs that the client uses to request additional pages from the search set. For a simple RESTful search, the page links are contained in the returned bundle as links. See the [core specification] for more information

------------------------------------------------------------------------

  [core specification]: http://hl7-fhir.github.io/search.html#return

  [FHIR RESTful API]: http://hl7.org/fhir/DSTU2/http.html
  [Searching]: http://hl7-fhir.github.io/search.html
  [Issue \#39]: https://github.com/argonautproject/implementation-program/issues/39
  [compartment]: http://hl7.org/fhir/DSTU2/compartments.html#compartments
  [core specification]: http://hl7-fhir.github.io/extensibility.html#2.20.0.2.2
  [DataAbsentReason Extension]: http://hl7-fhir.github.io/extension-data-absent-reason.html
  [http://hl7.org/fhir/StructureDefinition/data-absent-reason]: http://hl7.org/fhir/StructureDefinition/data-absent-reason
