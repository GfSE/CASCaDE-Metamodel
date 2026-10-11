## Constraints
All constraints must be satisfied in addition to the JSON-LD schemata, XML schemata or RDF shapes.

### General
- IDs are unique

### Model Integrity
- Property.type is owl:DatatypeProperty
- Property.specializes is a Property
- Property.datatype is a valid xs: datatype
- Property.maxLength is >0 and only specified, if datatype is xs:string
- Property.pattern is a regular expression and only specified, if datatype is xs:string
- Property.minInclusive is only specified, if datatype is a number
- Property.maxInclusive is only specified, if datatype is a number
- Property.minInclusive is smaller or equal Property.maxInclusive
- Property datatype and range must be a super-set of those defined in the specialized Property (following the restrictions of OWL)
- Property.defaultValue meets datatype and range
- Property.composes entries are each pointing to a Property
- Property.composes chain is a tree (without cyclic dependency)
- Link.type is owl:ObjectProperty
- Link.specializes is a Link
- Link.enumeratedEndpoint entries point to either 1 Enumeration, 1..n Entities *or* 1..n Relationships
- Link.defaultValue is a valid Id-string (URI or UUID with namespace)
- Link.enumeratedEndpoints must be a super-set of those defined in the specialized Link (following the restrictions of OWL)
- Enumeration.type is owl:Class
- Enumeration.specializes is an Enumeration
- Enumeration.enumeratedValue complies with the datatype
- Entity.type is owl:Class
- Entity.specializes is an Entity
- Entity.enumeratedProperty entries are each pointing to a Property
- Entity.enumeratedTargetLink entries are each pointing to a Link
- Entity.enumeratedProperty and Entity.enumeratedTargetLink entries are super-sets of those defined in the specialized Entity.
- Relationship.type is owl:Class
- Relationship.specializes is a Relationship
- Relationship.enumeratedProperty entries are each pointing to a Property
- Relationship.enumeratedSourceLink has exactly one entry pointing to a Link
- Relationship.enumeratedTargetLink has exactly one entry pointing to a Link
- Relationship.enumeratedProperty, Relationship.enumeratedSourceLink and Relationship.enumeratedTargetLink entries are super-sets of those defined in the specialized Relationship.
- aProperty is contained in a parent aPackage, anEntity or aRelationship
- aProperty.type is a Property
- aProperty.type is contained in enumeratedProperty list of its parent's type (Entity or Relationship)
- aProperty minCount and maxCount are met, language-aware in case of xs:string
- aProperty.value is a multilanguage object in case of xs:string, where the language tag is set if more than 1 language is provided
- aProperty.value is a simple value (literal) in case the datatype is other than xs:string
- aProperty.value meets the datatype of its type
- aProperty.composes entries are aProperty
- aSourceLink is contained in a parent aRelationship
- aSourceLink.type is a Link
- aSourceLink.type is contained in the enumeratedSourceLink list of its parent's type (Relationship)
- aSourceLink.hasEndpoint (idRef) points to an instance of an entry listed as enumeratedSourceLink of its type (Link).
- aTargetLink is contained in a parent aPackage, anEntity or aRelationship
- aTargetLink.type is a Link
- aTargetLink.type is contained in enumeratedTargetLink list of its parent's type (Entity or Relationship)
- aTargetLink.hasEndpoint (idRef) points either to an instance of an entry listed as enumeratedTargetLink of its type (Link) or to an enumeratedValue of the listed Enumeration
- aPackage.type is an Entity
- aPackage.context defines all namespace prefixes used in its (sub-) graph
- anEntity.type is an Entity
- aRelationship.type is a Relationship
- A specializes chain is a tree (without cyclic dependency)
