## Real-service play-loop smoke test

Set `USE_REAL_SERVICES=true` to point the play-loop suite at the local `studio/server` contract. The GitHub Actions smoke job is opt-in through the repository variable `COUGR_TESTNET_SMOKE=true` and uses `continue-on-error` so testnet latency or friendbot availability never blocks required gates.

Local usage:

```sh
cd studio
npm ci
USE_REAL_SERVICES=true npm test -- --runInBand tests/play-loop.spec.ts
```

The service must expose `/friendbot`, `/reconfigure`, `/state`, and `/rpc/move` with the shapes documented by the play-loop fixtures.
