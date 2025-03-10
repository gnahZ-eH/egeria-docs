<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ODPi Egeria project. -->

# Discovery Annotations

A discovery annotation describes one or more related properties about an
[Asset](/egeria-docs/concepts/asset) that has been
discovered by a [discovery service](discovery-service.md).

Some discovery annotations refer to an entire asset and others refer to a data field within
an asset.   The annotations that describe a single data field are called *data field annotations*.

The annotation types defined in the  [Open Discovery Framework (ODF)](/egeria-docs/frameworks/odf/overview) are as follows:

* **Classification Annotation** - Captures a recommendation of which classifications to
  attach to this asset.  It can be made at the asset or data field level.
* **Data Class Annotation** - Captures a recommendation of which data class this data field
  closely represents.
* **Data Profile Annotation** - Capture the characteristics of the data values stored in a specific
  data field in a data source.
* **Data Profile Log Annotation** - Capture the named of the log files where profile
  characteristics of the data values stored in a specific data field.  This is used when the profile
  results are too large to store in open metadata.
* **Data Source Measurement Annotation** - collect arbitrary properties about a data source.
* **Data Source Physical Status Annotation** - documents the physical characteristics of a data source asset.
* **Relationship Advice Annotation** - document a recommended relationship that should be established with
  the asset.
* **Quality Annotation** - document calculated quality scores on different dimensions.
* **Schema Analysis Annotation** - document the structure of the data (schema) inside the asset.
* **Semantic Annotation** - documents suggested meanings for this data based on the values and name
  of the field.
* **Suspect Duplicate Annotation** - identifies other asset definitions that seem to point to the same physical
  asset.

## Open Metadata Types for Discovery Annotations

The open metadata types for a discovery annotations are describe in
[Area 6](/egeria-docs/types/6).

The main entity type is called
[Annotation](/egeria-docs/types/6/0610-Annotations).
It is extended by
[DataFieldAnnotation](/egeria-docs/types/6/0617-Data-Field-Analysis.md)
to distinguish annotations that refer, primarily to a data field.
Other more specialist annotations extend these two basic annotation types.


---8<-- "snippets/abbr.md"