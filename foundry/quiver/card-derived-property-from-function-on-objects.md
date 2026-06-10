---
source_url: "https://www.palantir.com/docs/foundry/quiver/card-derived-property-from-function-on-objects/"
title: "Derived property from function on objects"
---
# Derived property from function on objects

Add a new transform table column backed by a Foundry function. The new column can be of type boolean, string, number, or time, depending on the output of the function. To use a function in this transform, it must satisfy the following requirements: The function input parameters must include an ObjectSet<ObjectType> parameter (and can optionally include other input parameters). The function return type must be a FunctionsMap<ObjectType, CustomType>. The FunctionsMap keys are objects with object IDs matching those in the table. The FunctionsMap values are primitives. See Function-backed columns for more information. When defining a function that returns a numerical value, we recommend returning either Double or Integer over Float. Input type. String, number, time, boolean. Output type. String. Usage information. FunctionalityAvailability Standard Quiver card. Unsupported. Transform table transform. Supported.
