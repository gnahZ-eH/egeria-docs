---
hide:
- toc
---

<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project. -->

--8<-- "snippets/content-status/tech-preview.md"

# Database Integrator Open Metadata Integration Service (OMIS)

The Database Integrator OMIS supports the exchange of data assets and their related schema and
connection information between an external relational database manager
and the open metadata ecosystem.

It supports a type of [integration connector](/egeria-docs/concepts/integration-connector)
that are able to create [Database](/egeria-docs/types/2/0224-Databases)
and [DeployedDatabaseSchema](/egeria-docs/types/2/0224-Databases)
assets along with is associated [tables and columns](/egeria-docs/types/5/0534-Relational-Schemas).
Optionally, this metadata can be tied to a [Database Manager](/egeria-docs/types/2/0224-Databases)
also known as a Database Management System (DBMS).

Figure 1 shows the types of metadata that integrators connectors can create with this integration service.

![Figure 1](/egeria-docs/services/omas/data-manager/relational-database-model.svg)
> **Figure 1:** Database metadata supported by the Database Integrator OMIS 

The structure of a database schema consist of a number of database tables and database views.
The difference is that the database table has its values stored in the database whereas the
database view is a set of values that are derived from accessing other
database tables using a query.

The structure of both the database tables and database views are describes by database columns.

Database columns have a types that represent a single value.  This can be stored, or derived using a query.
If the column presents the unique for a row within the table, it can be decorated with the
[PrimaryKey](/egeria-docs/types/5/0534-Relational-Schemas) classification.
If a column contains values that are the primary key of another table then the two columns can be linked using the
[ForeignKey](/egeria-docs/types/5/0534-Relational-Schemas) relationship.

Figure 2 shows the open metadata types used to represent the metadata created through this service.

![Figure 2](/egeria-docs/services/omas/data-manager/relational-database-open-metadata-types.svg)
> **Figure 2:** Database open metadata types supported by the Database Integrator OMIS 

A database schema is represented using the
[DeployedDatabaseSchema](/egeria-docs/types/2/0224-Databases) entity,
the database table is represented using the 
[RelationalTable](/egeria-docs/types/5/0534-Relational-Schemas) entity
and the database column is represented using the 
[RelationalColumn](/egeria-docs/types/5/0534-Relational-Schemas) entity.
A database view is a 
[RelationalTable](/egeria-docs/types/5/0534-Relational-Schemas) entity
with the [Calculated Value](/egeria-docs/types/5/0512-Derived-Schema-Elements)
classification attached.

If a DatabaseManager is defined, any Database created is automatically linked to it using the
[ServerAssetUse](/egeria-docs/types/0/0045-Servers-and-Assets)
relationship.
When a DeployedDatabaseSchema is created for the Database,
the service automatically inserts the
[DataContentForDataSet](/egeria-docs/types/5/0503-Asset-Schema) relationship.
(The database schema is a DataSet over the database which is a type of DataStore).

When a RelationalTable is created for the DeployedDatabaseSchema,
the service automatically inserts the
[AssetSchemaType](/egeria-docs/types/5/0503-Asset-Schema) relationship,
[RelationalDBSchemaType](/egeria-docs/types/5/0534-Relational-Schemas) entity and
[AttributeForSchema](/egeria-docs/types/5/0505-Schema-Attributes) relationship
in between the DeployedAPI entity and the RelationalTable entity.

The SchemaType for a RelationalTable is [RelationalTableType](/egeria-docs/types/5/0534-Relational-Schemas).
The schema attributes for RelationalTable and RelationalColumn also use
the [TypeEmbeddedAttribute](/egeria-docs/types/5/0505-Schema-Attributes)
classification [method for defining the schema type](/egeria-docs/guides/developer/mapping-technology/modelling-schemas).

This integration service is paired with the [Data Manager OMAS](/egeria-docs/services/omas/data-manager/overview).

---8<-- "snippets/abbr.md"