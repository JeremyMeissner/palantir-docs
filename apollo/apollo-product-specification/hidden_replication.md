---
source_url: "https://www.palantir.com/docs/apollo/apollo-product-specification/hidden_replication/"
title: "Replication [Beta]"
---
# Replication [Beta]

Replication [Beta] Replication is in a beta state and may not be available on your Apollo Hub. Contact your Palantir representative to learn more. This portion of the specification details how services can declare the number of replicas the infrastructure should create for the service. Default Product Configuration. Developers may declare the number of replicas for their service within a configuration.yml's top-level replication field: 1 2 replication: desired: 3. The desired field must be an integer value greater than 0. Default product configurations should include replication configuration. The default production configuration's replication.desired value may be overridden when configuring specific installations of a product as needed. If replication is defined in neither product default configuration nor an installation's configuration overrides, a default value of 2 is used.
