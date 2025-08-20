# HIP-10: Chronos Job Templates & Auto-Refill
- **Status**: Draft
- **Category**: Interface / Meta
- **Authors**: @FCPIDZ213
- **Created**: 2025-08-20
- **Requires**: HD-10

## Summary
One-click Chronos templates plus a small encoding helper and a simple Auto-Refill flow for the cron wallet. Goal: lower friction, reduce errors, and increase on-chain activity/XP.

## Motivation
Job creation is too technical (ABI, calldata, deposits). Lowering the barrier drives more scheduled tasks, TXs, and Chronos mission completion.

## Specification
### Templates
- `ChronosCounter`: `run()` increments a counter (heartbeat).
- `TokenDrip`: periodic fixed transfer to a target address.
- `KeepAlive`: writes a heartbeat state for monitoring tools.
- `HealthPing`: emits `Alive(n,timestamp)` event.
- `WebhookRelay (stub)`: emits an event for an off-chain relayer.

### Registration Helper
- `CronHelper.create(target, fn, freq, gasLimit, maxGasPrice)` (payable deposit) encodes `fn()` and calls the Chronos precompile — no raw ABI JSON pasted.
- Remix + ethers CLI snippets provided.

### Auto-Refill
- Minimal UI top-up for the cron wallet + low-balance alert (<0.02 HLS).
- Clear refund path documented.

### Defaults
- frequency ≥ 10 blocks, gasLimit 400k, maxGasPrice ≈ 2–3 gwei.

## Security / Compatibility
No protocol change; base templates avoid external calls; rate limits/quotas to mitigate spam.

## Test Plan
Unit tests; e2e on testnet (≥100 successful executions); explorer checks for events/counters; failure cases (low balance, bad params).

## Rollout & KPIs
W1: merge templates + docs; W2: add UI top-up.  
**KPIs:** jobs/day, Chronos mission completion %, refund rate.
