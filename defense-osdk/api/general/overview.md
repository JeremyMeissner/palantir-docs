---
source_url: "https://www.palantir.com/docs/defense-osdk/api/general/overview/"
title: "Palantir Defense OSDK \u2022 API Reference"
---
To enable Joint All-Domain Command and Control (JADC2), the U.S. military and its allies and partners rely heavily on the organizational and institutional efforts necessary to:

* Ensure Joint Force and partner nation interoperability;
* Modernize training and doctrine to prepare its personnel to fully leverage next generation JADC2 capabilities; and
* Secure the budgetary resources necessary to develop and deploy its foundational technology and infrastructure.

Central to the final element in that list is the ability to integrate, understand, and derive decision dominance from a legion of disparate source systems across warfighting functions that, in its end state, will connect *sensors* to *shooters* to *sustainers* at echelon. To help orient the defense software industrial base around the challenge of data model complexity across Joint Force and partner nation systems while providing an API surface for third-party application development, Palantir developed the Defense OSDK resulting from the functional expertise continuously honed supporting the Army, Air Force, Navy, Marine Corps, and the Combatant Commands across [several domains central to military doctrine](#defense-osdk-domains).

## What is the Defense OSDK?

Developed as an API to abstract away the need to understand complex, heterogenous, and disparate data models across warfighting functions and domains, Palantir’s Defense OSDK provides an explicit, semantically consistent data layer that is consumable by third-party applications from the environments in which they are built. Palantir persistently modifies the Defense OSDK alongside the Services to ensure its types serve as a trusted foundation, as opposed to a static data model, upon which third-parties develop and deploy operational applications that strengthen the military's most flexible tool: its software.

[Learn more about the Ontology in Foundry](/docs/foundry/ontology/overview/).

## Use the Ontology SDK to interact with Defense Ontology data

The [Ontology SDK](/docs/foundry/ontology-sdk/overview/) provides access to the Defense OSDK and its [interfaces](/docs/foundry/interfaces/interface-overview/) to extend third-party applications from where they are developed. The Ontology SDK grants ergonomic access to Ontology APIs, generates only relevant functions and types for querying, provides TypeScript bindings to enable rapid React application development, and is secured by a token scoped precisely to the ontological entities a third-party application should access based on its intersection with your own permissions to the Ontology’s backing data.

[Interfaces](/docs/foundry/interfaces/interface-overview/) describe an [object type's](/docs/foundry/object-link-types/object-types-overview/) shape and capabilities to ensure consistent modeling of and interaction with object types that share a common shape. Composed of [shared properties](/docs/foundry/object-link-types/shared-property-overview/), [link types](/docs/foundry/object-link-types/link-types-overview/), and their [metadata](/docs/foundry/object-link-types/link-type-metadata/), interfaces provide type safety and enable users to interact with the Ontology without knowledge of or familiarity with its object types or their underlying data models. Interfaces can be implemented by multiple object types, extended with other interfaces as a means of composability, and conceptualized as an API layer enabling third-party applications to interact with the Defense OSDK *without* the need to support each individual object type.

Interfaces are inherently abstract, and their schemas are defined only by shared properties. Unlike object types, they do not contain a backing dataset and cannot be instantiated. Rather, interfaces help third-party builders reuse code by defining the shape of a virtual object and its properties which concrete object types implement. As an example, a developer building an Ontology SDK-driven React application plotting real-time location data for a unit's major end items could simply reference in its code a `Major End Item` interface that contains geotemporal properties shared and implemented by distinct object types representing multiple major end item object types, such as `Tank`, `Humvee`, or `Aircraft`.

To develop against the Defense OSDK, generate an Ontology SDK client using Foundry’s [Developer Console](/docs/foundry/ontology-sdk/create-a-new-osdk/). Once generated, Developer Console creates packages documenting the endpoints available to consume all relevant Ontology entities selected during the client creation process using TypeScript, Python, Java, or cURL.

[Learn more about application building on top of Palantir Ontologies using the Ontology SDK](/docs/foundry/ontology-sdk-react-applications/overview/).

## Use Palantir’s platform APIs to interact with Foundry and Gotham applications

While the Ontology SDK ensures third-party developers can treat Foundry as their application’s backend, Palantir’s platform-specific APIs, tailored to enable JADC2 workflows as their own SDK, enable interactions with Foundry and Gotham applications. Review the sample [React ↗](https://react.dev/) applications in the [Defense SDK's GitHub repository ↗](https://github.com/palantir/defense-sdk-examples). To begin developing with Palantir’s platform APIs, [create a bearer token](/docs/foundry/api/v2/general/overview/authentication/). To leverage these APIs in production applications, create a confidential client in Developer Console using a similar workflow required for the Ontology SDK. [Learn more about using platform APIs alongside the Defense OSDK ↗](https://www.palantir.com/defense/sdk/).

[You can garner direct access to the Defense OSDK to explore its structure and capabilities or schedule a Defense OSDK Bootcamp by submitting a request to start building ↗](https://www.palantir.com/request-defense-osdk).

---

## Defense OSDK domains

Select a Defense OSDK domain to learn more about the interfaces which serve as abstract representations of its component real-world entities and the complex relationships between their properties.

- [**Common interfaces across domains**](/docs/defense-osdk/api/common/overview/about/)
- [**Intelligence**](/docs/defense-osdk/api/intelligence/overview/about/)
- [**Mission Planning**](/docs/defense-osdk/api/missionPlanning/overview/about/)
- [**Order of Battle**](/docs/defense-osdk/api/orderOfBattle/overview/about/)
- [**Targeting and Fires**](/docs/defense-osdk/api/targetingFires/overview/about/)
