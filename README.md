# fixin8r-global

Global resources and things for fixin8r services

# Overview

```mermaid
graph TD
    Alertmanager -->|Sends alerts| Gatekeeper
    Gatekeeper -->|Writes to| KafkaTopic["Kafka Topic: alerts-raw"]
    KafkaTopic -->|Read by| Router["fixin8r-router"]
    Router -->|Queries| Consul
    Router -->|Conditionally Writes to| AlertsTopic["Kafka Topic: alerts"]
    AlertsTopic -->|Read by| Remediationator["fixin8r-ticketer"]
    AlertsTopic -->|Read by| Ticketer["fixin8r-remediationator"]
```