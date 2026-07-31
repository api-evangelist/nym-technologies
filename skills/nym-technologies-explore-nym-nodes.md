---
name: Explore Nym nodes and families
description: Enumerate bonded and described Nym nodes, inspect a node's performance and stake saturation, and resolve its node family from the public Nym API.
api: openapi/nym-technologies-nym-api-openapi.json
operations: [get_bonded_nodes, get_described_nodes, rewarded_set, get_current_node_performance, get_node_stake_saturation, get_families, get_family_for_node]
---

# Explore Nym nodes and families

The Nym API is a public read API. Base URL: `https://validator.nymtech.net/api`. List endpoints accept `page` and `per_page` query parameters.

## Steps

1. List bonded nodes with `get_bonded_nodes` (`GET /v1/nym-nodes/bonded`), paging with `page`/`per_page`.
2. Get self-described node metadata with `get_described_nodes` (`GET /v1/nym-nodes/described`).
3. See which nodes are in the active rewarded set with `rewarded_set` (`GET /v1/nym-nodes/rewarded-set`).
4. For a specific `node_id`, read `get_current_node_performance` (`GET /v1/nym-nodes/performance/{node_id}`) and `get_node_stake_saturation` (`GET /v1/nym-nodes/stake-saturation/{node_id}`).
5. Resolve grouping: `get_families` (`GET /v1/node-families`) lists families; `get_family_for_node` (`GET /v1/node-families/by-node/{node_id}`) maps a node to its family.

## Conventions and errors

- A `400` on an identity/node lookup usually means an invalid base58 ed25519 key — validate the key format first. See `conventions/nym-technologies-conventions.yml` and `errors/nym-technologies-problem-types.yml`.
- Prefer `/v1/nym-nodes/*` over deprecated `/v1/legacy/*` and `/v1/unstable/*` paths.
