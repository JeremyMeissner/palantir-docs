---
source_url: "https://www.palantir.com/docs/apollo/managing-entities/stopping-and-starting-entities/"
title: "Stopping and Starting Entities"
---
# Stopping and Starting Entities

In Kubernetes, a live pod cannot be paused and restarted in the traditional sense. However, the number of replicas can be set to 0 to stop all instances. Increasing the number of replicas to a non-zero value will then "restart" the service. You can stop and restart Entities within a given Environment in Apollo by setting the replicas to 0 in the configuration overrides. To restart a stopped service, remove the configuration that sets replicas to 0 to set the replicas back to the Product's default. An example override to set replicas to 0 is provided below. This example override sets the desired replicas of this Entity to be 0 (specifically, all 2.x.x versions greater than or equal to 2.2.0). 1 2 3 4 "2.2.0": live-reloaded-config: replication: desired: 0. Learn more about setting config overrides.
