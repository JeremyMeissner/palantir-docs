---
source_url: "https://www.palantir.com/docs/foundry/foundryts/search-property/"
title: "foundryts.search.Property"
---
# foundryts.search.Property

class foundryts.search.Property(name, property_type, field, should_normalize=False, force_analyze=False). A FoundryTS wrapper for an Ontology object property. This class is used internally for evaluating Search queries. As a result of ontology(), instances of Property will be evaluated for Search expressions. Parameters: name (str) – Name of the Ontology object property. property_type (type) – The type of values in the property as a Python time. Review corresponding supported types in the ↗ Platform documentation. should_normalize (bool , optional) – Whether to normalize the name of the Ontology property. (default is False). force_analyze (bool , optional) – (DEPRECATED) Whether to reference raw properties. (default is False).
