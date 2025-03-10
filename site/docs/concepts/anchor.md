---
hide:
- toc
---

<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the Egeria project. -->

# Anchor

An *anchor* is a [Referenceable](/egeria-docs/concepts/referenceable) metadata entity that
groups other entities together as if they were logically a part of the anchor.
This means, for example, if the anchor entity is deleted then
the entities anchored to this entity are also deleted.

The value of establishing this grouping is to ensure that entities that have little meaning without their
anchor entity are cleaned up properly and are not left to uselessly clutter the repository.

!!! example "Example: personal messages and profiles"
    For example, if a [personal message](/egeria-docs/concepts/personal-message) is attached to
    a [personal profile](/egeria-docs/concepts/personal-profile) then that personal profile is its anchor.
    If the personal profile is deleted then the personal message is deleted too.

Anchored entities are also bound by the visibility and security restrictions of their anchor. 

!!! example "Example: Assets"
    For example, [Asset](/egeria-docs/concepts/asset) visibility is controlled by [governance zones](/egeria-docs/concepts/governance-zone).
    An Asset is only visible through a service if it is a member of that service's **supportedZones**.  Similarly,
    authorization to perform specific operations on an Asset is granted by the
    [Open Metadata Security Services](/egeria-docs/features/metadata-security).
    When a [SchemaType](/egeria-docs/types/5/0501-Schema-Elements/#schematype) is attached to an Asset, it is anchored to that Asset.
    Subsequent requests to read or update the SchemaType will result in visibility
    and authorization checks for the requesting user being made with respect to its Asset anchor.

The anchor grouping is limited to particular types of metadata entities that are only
meaningful in the context of their anchor entity.
So not all metadata entities linked to an anchor are anchored to it. They have an independent
existence and may be linked to many anchors, without obligation.

!!! example "Example: personal profiles and Assets"
    For example, a personal profile may contain links to specific "favorite" Assets.
    When the personal profile is deleted, the assets are not effected - except that they lose
    their relationship to the personal profile.

# Anchors classification

The [Anchors](/egeria-docs/types/0/0010-Base-Model/#anchors) classification makes it easier to find the anchor entity.
It is attached to any anchored entity.

!!! example "Example: SchemaElements and Comments"
    In the example above, Anchors would be on all the SchemaElements and Comments.
    Anchors would contain the unique identifier (GUID) of the anchor Referenceable.
    There is also the unique identifier (GUID) of the SchemaType at the root of a schema structure and the
    unique identifier (GUID) of the Comment at the root of a comment tree to make it easier to process these elements
    as a group.

    Following is an illustration of this example, with the addition of an Asset.
    The entities that have the Anchors classification are those that are
    anchored to the Asset.
    This includes entities such as Ratings, Likes and Attachments
    (from the [Open Discovery Framework (ODF)](/egeria-docs/frameworks/odf/overview).
    It is worthwhile maintaining the Anchors classification because reads of and updates to the anchored
    entities will happen many times, and it is rare that an anchored entity will change its anchor during its lifetime.

    ![Examples of dependent entities that are anchored to an Asset](anchors-classifications-on-dependant-objects.svg)

If a [GlossaryTerm](/egeria-docs/concepts/glossary-term), or [InformalTag](/egeria-docs/concepts/informal-tag)
is attached to the Asset, they are not anchored to it.
GlossaryTerms and InformalTags are independent entities.
They are not anchored to the Asset and hence do not have an Anchors classification.
Any change to these entities does not reflect in the LatestChange classification of the Asset.
However, the act of attaching them to, or detaching them from the Asset is recorded
in the Asset's LatestChange classification. Since the GlossaryTerm is also an anchor,
when the GlossaryTerm and the Asset are linked
together, this change is reflected in both of their LatestChange classifications because
they are both Referenceable anchors.

NoteLogs are Referenceables that can be attached to many other Referenceables.
They can be set up either to be anchored with a single Referenceable or to
be their own anchor to allow then to be attached to and detached from
many Referenceables over its lifetime.

!!! example "Example: NoteLog and Referenceables"
    For example, these are cases where the [NoteLog](/egeria-docs/concepts/note-log) is anchored to another Referenceable

    - NoteLogs are used to support the personal blog linked off of the Personal Profile in Community Profile OMAS.
    - Assets may have a NoteLog to record "news" for consumers such as planned maintenance and unexpected situations.

    Egeria uses the Anchors classification on a NoteLog to indicate that the NoteLog is tied to the Referenceable it is attached to. 
    The presence of this classification would prevent it from being linked to another Referenceable.

    Following is an illustration of the additional objects connecting to an asset that do not have the Anchors classification
    because they are not anchored to the Asset.
    Also notice there are two NoteLogs attached to the asset,
    one with the Anchors classification and one without.
    The one with the Anchors classification is anchored to the the Asset. The one without the Anchors classification is
    independent of the Asset.

    ![Examples of other types of entities that are linked to an Asset but not necessarily anchored there](anchors-classifications-on-attached-objects.png#pagewidth)

!!! education "Further information"
    - [Anchor Management](/egeria-docs/features/anchor-management/overview) provide support for the Anchors and LatestChange classifications.

--8<-- "snippets/abbr.md"
