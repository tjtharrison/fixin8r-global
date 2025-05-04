# fixin8r-global

Global resources and things for fixin8r services


# Overview

```mermaid
graph TD
    Alertmanager -->|Sends alerts| Gatekeeper["fixin8r-gatekeeper"]
    Gatekeeper -->|Writes to| KafkaTopic["Kafka Topic: alerts-raw"]
    KafkaTopic -->|Read by| Router["fixin8r-router"]
    Router -->|Writes to| AlertsTopic["Kafka Topic: alerts"]
    Router -->|Writes to| RemediatesTopic["Kafka Topic: remediates"]
    AlertsTopic -->|Read by| Ticketer["fixin8r-ticketer"]
    RemediatesTopic -->|Read by| Remediationator["fixin8r-remediationator"]
```