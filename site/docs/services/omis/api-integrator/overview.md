---
hide:
- toc
---

<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project. -->

--8<-- "snippets/content-status/in-development.md"

# API Integrator Open Metadata Integration Service (OMIS)

The API Integrator OMIS supports the exchange of data assets and their related schema and
connection information between an external API manager
and the open metadata ecosystem.

It supports a type of [integration connector](/egeria-docs/concepts/integration-connector)
that is able to create [DeployedAPI](/egeria-docs/types/2/0212-Deployed-APIs)
assets along with its associated API specification ([APISchemaType](/egeria-docs/types/5/0536-API-Schemas)).
Optionally, this metadata can be tied to an [APIManager](/egeria-docs/types/0/0050-Applications-and-Processes).

Figure 1 shows the types of metadata that integrators connectors can create with this integration service.

![Figure 1](/egeria-docs/services/omas/data-manager/api-model.svg)
> **Figure 1:** API metadata supported by the API Integrator OMIS 

The structure of an API specification consist of a number of 
[APIOperation](/egeria-docs/types/5/0536-API-Schemas)s
which in turn have optional
[APIParameterList](/egeria-docs/types/5/0536-API-Schemas)s
for the header, request and response.
The details of these payloads are described using
[SchemaAttributes and SchemaTypes](/egeria-docs/guides/developer/mapping-technology/modelling-schemas).

Figure 2 shows the open metadata types used to represent the metadata created through this service.

![Figure 2](/egeria-docs/services/omas/data-manager/api-open-metadata-types.svg)
> **Figure 2:** API open metadata types supported by the API Integrator OMIS 

If an APIManager is defined, any API created is automatically linked to it using the
[ServerAssetUse](/egeria-docs/types/0/0045-Servers-and-Assets)
relationship.
When an APIOperation is created for the API,
the service automatically inserts the
[AssetSchemaType](/egeria-docs/types/5/0503-Asset-Schema) relationship,
[APISchemaType](/egeria-docs/types/5/0536-API-Schemas) entity and
[APIOperations](/egeria-docs/types/5/0536-API-Schemas) relationship
in between the DeployedAPI entity and the APIOperation entity.

Any schema attributes created through this interface will use the
[APIParameter](/egeria-docs/types/5/0536-API-Schemas) subtype
to allow for find requests that only return schema information for APIs.  The schema attributes also use
the [TypeEmbeddedAttribute](/egeria-docs/types/5/0505-Schema-Attributes)
classification [method for defining the schema type](/egeria-docs/guides/developer/mapping-technology/modelling-schemas).


This integration service is paired with the [Data Manager OMAS](/egeria-docs/services/omas/data-manager/overview).

---8<-- "snippets/abbr.md"