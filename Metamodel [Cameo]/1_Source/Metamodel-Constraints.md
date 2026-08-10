## Constraints

### General
- IDs are unique
- namespace prefixes are defined in the context

### Referential Integrity
- Property.id is different from any of the native properties defined for all item types
- Property.hasClass is owl:DatatypeProperty (schema)
- Property.specializes is a Property
- Property.datatype is a valid xs: datatype
- Property.maxLength is >0 and only specified, if datatype is xs:string
- Property.pattern is a regular expression
- Property.minInclusive is only specified, if datatype is a xs: number datatype
- Property.maxInclusive is only specified, if datatype is a xs: number datatype
- Property.minInclusive is smaller or equal Property.maxInclusive
- Property datatype and range must be contained in those of the specialized Property (following the restrictions of OWL)
- Property.defaultValue meets datatype and range
- Property.composes entries are each pointing to a Property
- Property.composes chain is a tree (without cyclic dependency)
- Link.id is different from any of the native properties defined for all item types
- Link.hasClass is owl:ObjectProperty (schema)
- Link.specializes is a Link
- Link.enumeratedEndpoint entries point to either 1 Enumeration, 1..n Entities or 1..n Relationships
- Link.defaultValue is a valid Id-string (URI or UUID with namespace)
- Link.enumeratedEndpoints must be contained in or be subClasses of those of the specialized Link (following the restrictions of OWL)
- Enumeration.hasClass is owl:Class (schema)
- Enumeration.specializes is an Enumeration
- Enumeration.enumeratedValue comply with the datatype
- Entity.hasClass is owl:Class (schema)
- Entity.specializes is an Entity
- Entity.enumeratedProperty entries are each pointing to a Property
- Entity.enumeratedTargetLink entries are each pointing to a Link pointing either to 1 Enumeration, 1..n Entities or 1..n Relationships
- Relationship.hasClass is owl:Class (schema)
- Relationship.specializes is a Relationship
- Relationship.enumeratedSourceLink has exactly one entry pointing to a Link pointing either to 1..n Entities or 1..n Relationships
- Relationship.enumeratedTargetLink has exactly one entry pointing to a Link pointing either to 1..n Entities or 1..n Relationships
- aProperty is contained in a parent aPackage, anEntity or aRelationship
- aProperty.hasClass is a Property
- aProperty.hasClass is contained in enumeratedProperty list of its parent's class (Enumeration, Entity or Relationship)
- aProperty minCount and maxCount are met, language-aware in case of xs:string
- aProperty.value is represented/interpreted as string regardless of the datatype
- aProperty.value is a multilanguage object in case of xs:string, where the language tag is set if more than 1 language is provided
- aProperty.value datatype and range are met
- aProperty.composes entries are aProperty
- aSourceLink is contained in a parent aRelationship
- aSourceLink.hasClass is a Link
- aSourceLink.hasClass is contained in enumeratedSourceLink list of its parent's class (Relationship)
- aSourceLink.idRef points to an instance of the entries listed in its class' Link.enumeratedEndpoints
- aSourceLink must specify identifier and revision of the endpoints, if its class has revisionAware set to true
- aTargetLink is contained in a parent aPackage, anEntity or aRelationship
- aTargetLink.hasClass is a Link
- aTargetLink.idRef points either to an instance of the entries listed in its class' Link.enumeratedEndpoints or to an enumeratedValue of the listed Enumeration
- aTargetLink.hasClass is contained in enumeratedTargetLink list of its parent's class (Entity or Relationship)
- aTargetLink must specify identifier and revision of the endpoints, if its class has revisionAware set to true
- anEntity.hasClass is an Entity
- aRelationship.hasClass is a Relationship
- aPackage.hasClass is an Entity
- all specializes chains are a tree (without cyclic dependency)

### Limitations (to be discussed)
- Enumerations cannot be contained in a composed Property
- Links cannot be contained in a composed Property
- enumeratedEndpoints of a Link must be of the same item type (Enumeration, Entity or Relationship)
