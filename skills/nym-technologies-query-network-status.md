---
name: Query Nym network status
description: Check Nym API health and read live mixnet network state — current epoch, reward parameters, chain status, and NYM circulating supply — from the public Nym API.
api: openapi/nym-technologies-nym-api-openapi.json
operations: [health, network_details, chain_status, get_current_epoch, get_interval_reward_params, get_full_circulating_supply]
---

# Query Nym network status

The Nym API is a public, unauthenticated read API. Base URL: `https://validator.nymtech.net/api`. No API key or token is required.

## Steps

1. Confirm the API is healthy with `health` (`GET /v1/api-status/health`) before relying on downstream data.
2. Read overall network configuration with `network_details` (`GET /v1/network/details`).
3. Check the underlying Nyx chain with `chain_status` (`GET /v1/network/chain-status`).
4. Read the current rewarding epoch with `get_current_epoch` (`GET /v1/epoch/current`) and its economics with `get_interval_reward_params` (`GET /v1/epoch/reward_params`).
5. Read NYM token supply with `get_full_circulating_supply` (`GET /v1/circulating-supply`).

## Conventions and errors

- Responses are plain JSON; errors are plain descriptive bodies (not RFC 9457). See `errors/nym-technologies-problem-types.yml`.
- A `500` may indicate a transient condition (e.g. bloom filters disabled) — retry.
- No idempotency key is needed; all steps here are idempotent GETs.
