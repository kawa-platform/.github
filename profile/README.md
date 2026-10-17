# Kawa

**kawa is a gateway for Apache Kafka that enhances your clusters capabilities.**
It speaks the Kafka wire protocol, so every
existing client, whether a producer, a consumer, Kafka Streams or a command-line tool, connects to it unchanged. kawa
only steps in where a feature applies: it authenticates clients, checks requests against access rules, rewrites
virtual topic names and holds topic changes to your conventions. Everything else passes straight through to the
broker.

![kawa: Kafka clients and AI agents connect to kawa gateway, which adds authentication, RBAC, virtual topics, consume filters, governance in front of the Kafka cluster, with MCP for AI agents coming](../docs/kawa-platform.svg)

## What kawa adds to your cluster

- **Authentication**: SASL (`PLAIN`, `SCRAM-SHA-256`, `SCRAM-SHA-512`) and TLS client certificates. Clients need no
  principal on the cluster.
- **RBAC**: roles, groups and ACLs decide what each principal may do. The default is deny.
- **Virtual topics**: clients use stable topic names, independent of where the data physically lives.
- **Consume filters**: show each client only the records it should see, selected by header or by a CEL expression
  over decoded JSON or Avro records.
- **Governance**: enforce naming conventions for topics, consumer groups and transactional ids, and property
  conventions such as partition counts and topic configs, as rules written in CEL.
- **MCP (coming, not implemented yet)**: AI agents will inspect and manage the gateway through an MCP endpoint,
  authenticated and authorized as themselves.
- **Management**: Studio (web UI), a REST admin API and a Kubernetes operator (operator coming soon).

## Where do I start?

| I want to...                        | Go to                                                                                                                           |
|-------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| See kawa working in a few minutes   | [kawa-demo](https://github.com/kawa-platform/kawa-demo) (`make compose-up`)                                                     |
| Learn the concepts and configure it | [kawa-docs](https://github.com/kawa-platform/kawa-docs)                                                                         |
| Run it on Kubernetes                | [kawa-charts](https://github.com/kawa-platform/kawa-charts) and [kawa-operator](https://github.com/kawa-platform/kawa-operator) (coming soon) |
| Manage it from a web UI             | [kawa-studio](https://github.com/kawa-platform/kawa-studio)                                                                     |
| Work on the gateway itself          | [kawa-gateway](https://github.com/kawa-platform/kawa-gateway)                                                                   |

## Repositories

| Repository                                                        | What it is                                                                                           |
|-------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| [kawa-gateway](https://github.com/kawa-platform/kawa-gateway)     | The gateway (Java): Kafka protocol, authentication, RBAC, virtual topics, governance, admin API       |
| [kawa-studio](https://github.com/kawa-platform/kawa-studio)       | Studio, the web admin UI                                                                             |
| [kawa-operator](https://github.com/kawa-platform/kawa-operator)   | Coming soon: Kubernetes operator (Go) that manages virtual topics as `VirtualTopic` resources                     |
| [kawa-charts](https://github.com/kawa-platform/kawa-charts)       | Helm charts to install kawa and the operator                                                         |
| [kawa-docs](https://github.com/kawa-platform/kawa-docs)           | Documentation site                                                                                   |
| [kawa-demo](https://github.com/kawa-platform/kawa-demo)           | Mission-control demo on Docker Compose or minikube                                                   |
| [kawa-design](https://github.com/kawa-platform/kawa-design)       | Shared CSS design system for Studio and the docs                                                     |
| [kawa-agent-kit](https://github.com/kawa-platform/kawa-agent-kit) | Agent and skill definitions for working on kawa                                                      |