#### Complete Summary of the Mandatory Requirements

1.  At least one identifier in `Organization.identifier`
    -   NPI preferred
    -   Tax id is allowed
    -   Local id is allowed in addition to 'authoritative' identifier

1.  One status in `Organization.active`
1.  One name in `Organization.name` (MAY have additional names in `Organization.alias`)
1.  At least one contact in `Organization.telecom`
1.  At least one address in `Organization.address`
1.  At least one reference to Endpoint resource in `Organization.endpoint`
