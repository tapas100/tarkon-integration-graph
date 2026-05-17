# tarkon-integration-graph

The **Integration Graph** maintains a live, queryable graph of all service integrations, data contracts, and cross-service dependencies across the entire Tarkon platform.

---

## Responsibilities

- Build and maintain a graph of all service-to-service integrations
- Track API contracts, event schemas, and data types per edge
- Detect contract violations and breaking changes
- Provide impact analysis: "if service X changes, which services are affected?"
- Monitor integration health (latency, error rates per edge)
- Version-track all contracts with schema evolution history
- Feed integration data to `tarkon-architecture-intelligence`

---

## Tech Stack

| Layer         | Technology                       |
|---------------|----------------------------------|
| Language      | Python 3.12                      |
| Framework     | FastAPI                          |
| Graph DB      | Neo4j                            |
| Schema        | Pydantic + JSON Schema           |
| Monitoring    | Prometheus + OpenTelemetry       |
| Testing       | pytest                           |

---

## Project Structure

```
src/
  __init__.py
  api.py
  config.py
  graph/
    __init__.py
    neo4j_client.py
    integration_graph.py
    impact_analyser.py
  contracts/
    __init__.py
    schema_registry.py
    validator.py
    evolution_tracker.py
  monitoring/
    __init__.py
    health_collector.py
    metrics_aggregator.py
  models/
    __init__.py
    service_node.py
    integration_edge.py
    contract.py
  utils/
    __init__.py
tests/
  test_impact_analyser.py
  test_contract_validator.py
docs/
Dockerfile
podman-compose.yml   # includes Neo4j
```

---

## Quick Start

```bash
podman-compose up -d neo4j
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
uvicorn src.api:app --reload --port 9021
```

---

## License

MIT
