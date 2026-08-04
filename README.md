# Events (events)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Event-driven APIs catalog. This topic repo documents the landscape of brokers, streaming platforms, schema registries, and the specifications that standardize how events are described, transported, and stored. "Events" is the **broader category** that contains webhooks (HTTP callbacks) as one delivery surface; the dedicated webhooks repo zooms in on that slice.

**URL:** [Visit APIs.json URL](https://github.com/api-evangelist/events)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=topic-api-evangelist&utm_content=repo)

## Tags

 - Events, Event-Driven, Event Streaming, Messaging, Pub Sub, Brokers, CloudEvents, AsyncAPI, Topic

## Timestamps

- **Created:** 2026-05-22
- **Modified:** 2026-05-22

## Landscape

Event-driven APIs are organized along two axes.

**The model axis** answers "what shape of delivery?"

| Model | Behavior | Canonical implementations |
|-------|----------|---------------------------|
| Pub / sub | Many-to-many fan-out; every subscriber sees every event. | MQTT, NATS core, Azure Event Grid, Google Cloud Pub/Sub. |
| Queue | Point-to-point load balancing; one event consumed by exactly one worker. | IBM MQ, RabbitMQ (AMQP 0-9-1), Pulsar shared subscriptions, NATS queue groups. |
| Stream | Durable, ordered, partitioned commit log read by offset; replayable. | Apache Kafka, Apache Pulsar, Redpanda, AWS Kinesis, Pub/Sub Lite. |

**The spec axis** answers "what shape is on the wire and what describes it?"

| Layer | Spec | Owner | Role |
|-------|------|-------|------|
| Envelope | **CloudEvents 1.0.2** | CNCF (graduated 2024-01-25) | Standard wrapper around any event payload. Required attributes: `id`, `source`, `specversion`, `type`. |
| API description | **AsyncAPI** | Linux Foundation | Describes channels, operations, messages, and protocol bindings the way OpenAPI describes REST. |
| Payload schema | **JSON Schema 2020-12 / Avro / Protobuf** | JSON Schema org / Apache / Google | The shape of `data` inside a CloudEvent. Versioned in a schema registry. |
| Wire protocol | **Kafka / AMQP 1.0 / MQTT 5.0 / NATS / STOMP** | Apache / OASIS / OASIS / Synadia / GitHub | Bytes on the wire between producers, brokers, and consumers. |

A typical modern event flow looks like this:

```
Producer  ──CloudEvent────►  Broker  ──CloudEvent────►  Subscriber
   │                         (topic /                          │
   ▼                          channel)                         ▼
Schema Registry  ◄────── compatibility-checked ──────── Schema Registry
```

## Brokers and Streaming Platforms

### Open-Source Brokers

| Broker | Model | Protocol | Governance | Notable |
|--------|-------|----------|------------|---------|
| [Apache Kafka](https://kafka.apache.org) | Stream | Kafka | Apache Software Foundation | "Used by thousands of companies for high-performance data pipelines"; >80% of Fortune 100; KRaft replaces ZooKeeper. |
| [Apache Pulsar](https://pulsar.apache.org) | Queue + Stream | Pulsar binary | Apache Software Foundation | Multi-tenant by design (tenants / namespaces / topics), layered brokers + BookKeeper, current v4.2. |
| [NATS](https://nats.io) | Pub/sub + Queue Groups | NATS / JetStream | CNCF Incubating | Sub-ms latency single binary; JetStream adds persistence; 30+ community clients. |
| [Redpanda](https://redpanda.com) | Stream | Kafka API | Source-available (BSL) | C++, no JVM, no ZooKeeper; ships Connect + SQL; Redpanda Cloud. |
| [IBM MQ](https://www.ibm.com/products/mq) | Queue | MQI / JMS / AMQP / MQTT | IBM (commercial) | Enterprise messaging incumbent; current generation IBM MQ 9.4. |

### Managed Cloud Buses

| Service | Model | Protocols | CloudEvents |
|---------|-------|-----------|-------------|
| [AWS EventBridge](https://aws.amazon.com/eventbridge) | Pub/sub via buses + point-to-point pipes | HTTP push | Schema Registry supports OpenAPI / JSONSchema export. |
| [Azure Event Grid](https://azure.microsoft.com/en-us/products/event-grid) | Pub/sub (HTTP push & pull) + MQTT broker | HTTP, MQTT 3.1.1 / 5.0, MQTT over WS | Supports CloudEvents 1.0 natively alongside Event Grid schema. |
| [Google Cloud Pub/Sub](https://cloud.google.com/pubsub) | Pub/sub | gRPC + HTTP, push and pull subscriptions | Schemas (Avro, Protobuf), ordering keys, dead-letter topics, snapshot / seek. Pub/Sub Lite is the cheaper partitioned variant. |
| [Confluent Cloud](https://www.confluent.io/confluent-cloud) | Stream | Kafka | Built on Kora engine, 120+ pre-built / 90+ fully managed connectors, Tableflow, Confluent Cloud for Apache Flink, 99.99% multi-AZ SLA, runs on AWS / Azure / GCP. |

### Streaming Analytics SaaS

| Service | Engine | Role |
|---------|--------|------|
| [Tinybird](https://www.tinybird.co) | ClickHouse | Ingest events (HTTP Events API, up to 1,000 req/s; Kafka / S3 / GCS / Snowflake connectors); publish SQL pipes as APIs with sub-second latency. |
| [Materialize](https://materialize.com) | Differential dataflow | Streaming SQL with incremental view maintenance over Postgres + Kafka CDC sources; materialized views serve as live event streams. |

## Specifications

### CloudEvents

**CNCF graduated** specification (January 25, 2024). Current version **1.0.2**, with 1.0.3-wip in progress.

**Required context attributes**

| Attribute | Definition (quoted from spec) |
|-----------|-------------------------------|
| `id` | "Identifies the event. Producers MUST ensure that `source` + `id` is unique for each distinct event." |
| `source` | "Identifies the context in which an event happened." URI-reference. |
| `specversion` | The version of the CloudEvents specification the event uses. MUST be `"1.0"`. |
| `type` | "This attribute contains a value describing the type of event related to the originating occurrence." |

**Optional context attributes**: `datacontenttype`, `dataschema`, `subject`, `time`.

**Format bindings**: JSON (1.0.2), AVRO (1.0.2), Protobuf (1.0.2); XML and AVRO Compact in working draft.

**Transport bindings**: HTTP, Kafka, AMQP, MQTT, NATS, WebSockets.

**Subprojects**: CE SQL (v1.0.0 — query language for CloudEvents), Subscriptions API (working draft), xRegistry (registry / pagination spec, moved out of the spec repo).

### AsyncAPI

Linux Foundation specification covering: server, channel, operation, message, schema, binding, application, protocol, and the AsyncAPI document itself. Tooling: Generator, CLI, Studio, parsers in JS / Go / Java / Python / .NET. Acts as the event-driven counterpart to OpenAPI.

### Wire Protocols

| Protocol | Body | Standard? |
|----------|------|-----------|
| **MQTT 5.0** | Lightweight pub/sub for IoT; QoS 0/1/2; retained, last-will, persistent session. | OASIS standard. |
| **AMQP 1.0** | Binary protocol with nodes, links, sessions, frames. | OASIS standard + ISO/IEC 19464. |
| **STOMP 1.2** | Simple text-oriented protocol, often over WebSockets. | GitHub-hosted community spec. |
| **Kafka protocol** | TCP binary; the de facto streaming wire format. | Apache project, not a vendor-neutral standard. |
| **NATS protocol** | Text protocol over TCP; JetStream adds binary streaming. | Synadia / NATS project. |

## Schema Registries

| Registry | Backing | Artifact types | Notes |
|----------|---------|----------------|-------|
| [Confluent Schema Registry](https://docs.confluent.io/platform/current/schema-registry/index.html) | Confluent | Avro, JSON Schema, Protobuf | "Central repository with a RESTful interface ... to define standard schemas." Schema Linking syncs across hybrid / multicloud. |
| [Apicurio Registry](https://www.apicur.io/registry) | Red Hat (Apache 2.0) | OpenAPI, AsyncAPI, Avro, JSON Schema, Protobuf, Kafka Connect schema, GraphQL, WSDL, XSD | Storage backends: Kafka, PostgreSQL, MSSQL. Current 3.2.4. |

## Common Properties

- [Portal](https://github.com/api-evangelist/events)
- [GitHubOrganization](https://github.com/api-evangelist)
- [Vocabulary](vocabulary/events-vocabulary.yml)
- [JSONLD](json-ld/events-context.jsonld)

## Features

| Name | Description |
|------|-------------|
| Pub Sub Messaging | Many-to-many fan-out where each subscriber receives a copy of every event. |
| Queue Messaging | Point-to-point distribution where each event is consumed by exactly one worker. |
| Log Based Streaming | Durable, ordered, partitioned commit log read by offset; replayable. |
| Schema Governance | Schema registries version schemas and enforce compatibility so producers cannot break consumers. |
| CloudEvents Envelope | Standard required (`id`, `source`, `specversion`, `type`) plus optional (`datacontenttype`, `dataschema`, `subject`, `time`) attributes wrap any payload. |
| AsyncAPI Description | Document channels, operations, messages, and bindings the way OpenAPI documents REST. |

## Use Cases

| Name | Description |
|------|-------------|
| Microservice Integration | Decouple services so producers emit events without coupling to downstream consumers. |
| Change Data Capture | Replicate database changes onto Kafka, Pulsar, or Materialize for downstream consumers. |
| IoT Telemetry | Constrained devices publish readings over MQTT or NATS to cloud gateways such as Azure Event Grid or AWS IoT Core. |
| Real Time Analytics | Stream events into ClickHouse / Pinot / Druid-based platforms (Tinybird, Materialize) for sub-second dashboards. |
| Event Sourcing | Store every state change as an immutable event in a durable log so state can be rebuilt by replay. |
| Webhook Delivery | HTTP-based fan-out from a SaaS to subscriber URLs — the narrowest slice of the event landscape. |

## Integrations

| Name | Description |
|------|-------------|
| CloudEvents | Common envelope adopted across Azure Event Grid, Knative, and most CNCF event-emitting projects. |
| AsyncAPI | API description format used by Postman, Microcks, Apicurio, and many broker dashboards. |
| Kafka Protocol | De facto wire protocol; supported by Confluent Cloud, Redpanda, Aiven, and (via proxies) Azure Event Hubs and Pulsar. |
| MQTT | Native protocol for Azure Event Grid namespaces, AWS IoT Core, HiveMQ, EMQX, and Mosquitto. |
| Schema Registry | Confluent and Apicurio registries plug into Kafka serializers / deserializers in every major language client. |

## Solutions

| Name | Description |
|------|-------------|
| Open Source Brokers | Apache Kafka, Apache Pulsar, NATS, Redpanda Community, and RabbitMQ cover most self-hosted deployments. |
| Managed Cloud Buses | AWS EventBridge, Azure Event Grid, and Google Cloud Pub/Sub provide serverless event delivery within their respective clouds. |
| Managed Streaming SaaS | Confluent Cloud, Redpanda Cloud, Aiven for Kafka, and Tinybird offer fully managed Kafka or ClickHouse with their own consoles, APIs, and SLAs. |
| Specification Stack | CloudEvents (envelope) + AsyncAPI (API description) + JSON Schema / Avro / Protobuf (payload schema) compose into the standards layer brokers and registries implement. |

## Artifacts

Machine-readable descriptions of the event landscape.

### JSON Schema

- [CloudEvent](json-schema/events-cloudevent-schema.json) — CloudEvents 1.0 event record (required `id` / `source` / `specversion` / `type`; optional `datacontenttype` / `dataschema` / `subject` / `time`; `data` payload; extension attribute rules).
- [Event Source](json-schema/events-event-source-schema.json) — Descriptor for an event-emitting topic / channel / bus, with broker, protocol, partitioning, retention, delivery guarantee, ordering scope, CloudEvents `source` value, schema registry binding, AsyncAPI URL, ownership.
- [Event Subscription](json-schema/events-event-subscription-schema.json) — Descriptor for a subscription that consumes events: push / pull / stream delivery, filter expression, retry, dead-letter, consumer group, Pulsar subscription type, MQTT QoS.

### JSON-LD

- [Events Context](json-ld/events-context.jsonld) — aligns event vocabulary with `schema.org` (CloudEvent / EventSource / Broker / Producer / Consumer) and the CloudEvents and AsyncAPI namespaces.

### Examples

CloudEvents 1.0 payloads exercising common event shapes:

- [Order Placed](examples/events-order-placed-cloudevent-example.json) — synthetic commerce event with `subject`, `dataschema`, structured JSON payload.
- [S3 Object Created](examples/events-s3-object-created-cloudevent-example.json) — AWS-style event normalized into CloudEvents.
- [GitHub Pull Request Opened](examples/events-github-pull-request-opened-cloudevent-example.json) — wraps a GitHub webhook payload in the CloudEvents envelope.
- [MQTT IoT Telemetry](examples/events-mqtt-iot-telemetry-cloudevent-example.json) — sensor reading delivered over MQTT and represented as a CloudEvent.
- [Kafka Binary Mode](examples/events-kafka-binary-mode-cloudevent-example.json) — illustrates CloudEvents over Kafka with context attributes in record headers and the raw payload in the record value.
- [CloudEvents Batch Format](examples/events-cloudevents-batch-format-example.json) — JSON Batch serialization (an array of events).
- [Event Source Descriptor](examples/events-event-source-descriptor-example.json) — example instance of the Event Source schema for a Kafka topic.
- [Event Subscription Descriptor](examples/events-event-subscription-descriptor-example.json) — example instance of the Event Subscription schema with filter, retry, and dead-letter.

## Vocabulary

- [Events Vocabulary](vocabulary/events-vocabulary.yml) — operational dimension (actors, envelope, storage, protocols, delivery) and capability dimension (models, governance, formats, specifications, personas, workflows), plus broker, registry, and specification indexes.

## Notable Absences

- **No single OpenAPI** — the "events" topic isn't one API; it's a landscape. Each broker exposes its own management API (Kafka Admin, Pulsar Admin, EventBridge, Event Grid, Pub/Sub) under its own provider repo.
- **No AsyncAPI document at this level** — AsyncAPI describes a specific producer / consumer surface; this topic repo points at the spec, not an instance.
- **No commercial pricing or rate-limit artifacts** — those belong in the per-provider repos (Confluent Cloud, Redpanda Cloud, EventBridge, Event Grid, Pub/Sub, Tinybird, Materialize).

## Relationship to the Webhooks Topic

Webhooks are the narrowest delivery surface inside this landscape — HTTP push from a SaaS to a subscriber URL, almost always one event at a time, almost always without partitioning or replay. The api-evangelist `webhooks` topic repo zooms in on that surface (subscription management, signing, retry, replay), while this `events` repo covers the broader category and the brokers / specs that webhook delivery sits inside.

## Maintainers

**FN:** Kin Lane

**Email:** kinlane@gmail.com
