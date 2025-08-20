# HD-TBD: Chronos Job Templates & Auto-Refill
- **Status**: Draft
- **Authors**: @FCPIDZ213
- **Created**: 2025-08-20
- **Links**: Issue: https://github.com/helios-network/HIP/issues/9

## Context / Problem
Chronos is powerful but hard to use (ABI, calldata, deposits). This blocks adoption and on-chain activity.

## Objectives (Desiderata)
- [ ] Deliver 5 one-click templates (Counter, TokenDrip, KeepAlive, HealthPing, WebhookRelay stub).
- [ ] Provide a small helper (contract + script) to register a job without raw ABI JSON.
- [ ] Simple Auto-Refill flow for the cron wallet (top-up + low-balance alert).
- [ ] EN/FR docs + Remix & CLI examples.

## Expected Impact
More scheduled jobs per day, clear XP paths (Deployer/Farmer/Chronos mission), easier onboarding for Validators/Builders.

## Out of scope
Oracles/bridges in production; off-chain scheduler redesign.

## Risks & Mitigations
Spam → minimum frequency + quotas.  
Stuck deposits → refund flow + low-balance alert.
