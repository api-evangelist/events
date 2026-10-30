# Events

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Event-driven APIs catalog. Documents the landscape of brokers, streaming platforms, schema registries, and the specifications that standardize how events are described, transported, and stored. "Events" is the broader category that contains webhooks (HTTP callbacks) as one delivery surface, alongside message brokers, log-based streaming platforms, and managed pub/sub services. The catalog aligns around CloudEvents (CNCF graduated, v1.0.2) as the spec for the event payload envelope and AsyncAPI as the spec for the event API surface (channels, operations, messages, servers), and covers the major open-source brokers (Apache Kafka, Apache Pulsar, NATS, Redpanda, IBM MQ), cloud-native managed buses (AWS EventBridge, Azure Event Grid, Google Cloud Pub/Sub, Confluent Cloud), schema registries (Confluent Schema Registry, Apicurio Registry), and streaming-analytics SaaS (Tinybird, Materialize). Wire-level protocols included are MQTT (OASIS), AMQP (OASIS / ISO 19464), and STOMP.

**Areas:** Event · Event-Driven · Event Streaming · Messaging · Pub/Sub · CloudEvents · AsyncAPI · Topic · Message Broker

## Events on APIs.io

Everything profiled for Events is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/events/](https://apis.io/providers/events/)** — or go straight to one of the APIs or properties below.

### APIs (18)

- [CloudEvents](https://apis.io/apis/events/cloudevents/) — CNCF-graduated specification (graduated January 25, 2024) for describing event data in a common way. Defines a payload envelope with required attributes id,…
- [AsyncAPI](https://apis.io/apis/events/asyncapi/) — Linux Foundation-hosted specification for event-driven APIs. Describes servers, channels, operations, messages, schemas, and protocol bindings for Kafka,…
- [Apache Kafka](https://apis.io/apis/events/apache-kafka/) — Open-source distributed event streaming platform governed by the Apache Software Foundation. Described as used by "thousands of companies for…
- [Apache Pulsar](https://apis.io/apis/events/apache-pulsar/) — Open-source distributed messaging and streaming platform built for the cloud. Top-10 Apache Software Foundation project (740+ contributors, current version…
- [NATS](https://apis.io/apis/events/nats/) — CNCF incubating high-performance, lightweight messaging system designed for cloud, edge, and IoT. Supports pub/sub, request/reply, and queue groups over a…
- [Redpanda](https://apis.io/apis/events/redpanda/) — Kafka API-compatible streaming data platform written in C++ (no JVM, no ZooKeeper). Self-described as an "Agentic Data Plane and Data Streaming platform for…
- [IBM MQ](https://apis.io/apis/events/ibm-mq/) — Enterprise messaging middleware from IBM. Long the de facto standard for assured-once message delivery in regulated industries (banking, government).…
- [AWS EventBridge](https://apis.io/apis/events/aws-eventbridge/) — AWS serverless event router. "EventBridge is a serverless service that uses events to connect application components together, making it easier for you to…
- [Azure Event Grid](https://apis.io/apis/events/azure-event-grid/) — Azure's "highly scalable and fully managed publish-subscribe service for message distribution." Supports both HTTP push/pull delivery and an MQTT v3.1.1 /…
- [Google Cloud Pub/Sub](https://apis.io/apis/events/google-cloud-pubsub/) — Google Cloud's asynchronous and scalable messaging service that decouples message producers from consumers with typical latencies around 100 ms. Uses…
- [Confluent Cloud](https://apis.io/apis/events/confluent-cloud/) — Commercial managed service from Confluent positioned as "the industry's only fully managed data streaming platform." Built on the Kora cloud-native Kafka…
- [Confluent Schema Registry](https://apis.io/apis/events/confluent-schema-registry/) — Central repository with a RESTful interface for registering and evolving schemas in Avro, JSON Schema, and Protobuf. Enforces compatibility rules (backward,…
- [Apicurio Registry](https://apis.io/apis/events/apicurio-registry/) — Open-source schema and API artifact registry backed by Red Hat (Apache 2.0). Stores OpenAPI, AsyncAPI, Avro, JSON Schema, Protobuf, Kafka Connect schemas,…
- [Tinybird](https://apis.io/apis/events/tinybird/) — Managed ClickHouse-based SaaS for real-time analytics on event data. Ingests events via an HTTP Events API (up to 1,000 req/s) plus connectors for Kafka,…
- [Materialize](https://apis.io/apis/events/materialize/) — Streaming SQL database based on incremental view maintenance. Continually ingests CDC from Postgres, Kafka, and other sources, then keeps SQL views up to…
- [MQTT](https://apis.io/apis/events/mqtt/) — OASIS standard messaging protocol for the Internet of Things. Lightweight publish/subscribe transport for remote, constrained devices. Current version is…
- [AMQP](https://apis.io/apis/events/amqp/) — Advanced Message Queuing Protocol. AMQP 1.0 is both an OASIS standard and an International Standard (ISO/IEC 19464). Wire-level binary protocol defining…
- [STOMP](https://apis.io/apis/events/stomp/) — Simple (or Streaming) Text Oriented Messaging Protocol. Lightweight, text-based wire protocol for message-oriented middleware. Widely used as an alternative…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### GraphQL (1)

GraphQL schemas.

- [Moved to /providers/events/](https://apis.io/graphqls/events/events-graphql/)

#### JSON Schema (3)

The data models the API reads and writes.

- [CloudEvent](https://apis.io/schemas/events/events-cloudevent/)
- [Event Source](https://apis.io/schemas/events/events-event-source/)
- [Event Subscription](https://apis.io/schemas/events/events-event-subscription/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [Events Context](https://apis.io/jsonld/events/events-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Events Vocabulary](https://apis.io/vocabularies/events/events-vocabulary/)

#### Examples (7)

Example requests and responses.

- [Events Event Source Descriptor Example](https://apis.io/examples/events/events-event-source-descriptor-example/)
- [Events Event Subscription Descriptor Example](https://apis.io/examples/events/events-event-subscription-descriptor-example/)
- [Events Github Pull Request Opened Cloudevent Example](https://apis.io/examples/events/events-github-pull-request-opened-cloudevent-example/)
- [Events Kafka Binary Mode Cloudevent Example](https://apis.io/examples/events/events-kafka-binary-mode-cloudevent-example/)
- [Events Mqtt Iot Telemetry Cloudevent Example](https://apis.io/examples/events/events-mqtt-iot-telemetry-cloudevent-example/)
- [Events Order Placed Cloudevent Example](https://apis.io/examples/events/events-order-placed-cloudevent-example/)
- [Events S3 Object Created Cloudevent Example](https://apis.io/examples/events/events-s3-object-created-cloudevent-example/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Events — jsonschema rules](https://apis.io/rules/events/events-jsonschema-spectral-rules/)

#### Security (1)

Authentication, trust centre, and vulnerability disclosure.

- [Events Domain Security](https://apis.io/security/events/events-domain-security/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Blog](https://cloudevents.io/blog/)
- [GitHub](https://github.com/api-evangelist)

## API Evangelist rating

**Unrated** — no public website could be reached for this company, so there was almost nothing to measure and nothing a reader could check.

This is not a score of zero. No rating is published for this company. If that is wrong because something public exists that we missed, say so on this repository or email [info@apievangelist.com](mailto:info@apievangelist.com) and it will be re-run — free, and no justification needed.

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Events: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/events/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
