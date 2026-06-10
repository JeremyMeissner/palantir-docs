---
source_url: "https://www.palantir.com/docs/foundry/foundryts/search-ontology/"
parquet_url: "/foundry/foundryts/search-ontology/"
title: "foundryts.search.ontology"
fetched_at: "2026-05-12T19:34:36.036Z"
---
foundryts.search.ontology. foundryts.search.ontology(name, should_normalize=False, force_analyze=False). Creates an Ontology property reference for search. Use this for creating an Ontology property that you can compare values to in Search.series(). Parameters: name (str) – Name of the Ontology property as it appears in the Ontology. should_normalize (bool , optional *(*default is False )) – Whether to normalize the name of the Ontology property. force_analyze (bool , optional) – (DEPRECATED) Whether to reference raw properties. (default is False). Returns: The Ontology property reference that can be used in Search.series. Return type: Property. See Also. Search.series(). Examples. 1 2 3 4 5 >>> from foundryts.search import ontology >>> ontology('some-property-name') Property['some-property-name'] >>> fts.search.series(ontology('my_prop') == 'my_value') NodeCollection([...](1000)).
