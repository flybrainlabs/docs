# flybrainlabs v0.2 local testnet verification — 2026-09-14

Service: `http://127.0.0.1:8787/`, managed by the local `flypow-web` user service. This is a local coordinator, not a deployed P2P mainnet.

## Automated checks

- `cargo test --release`: 23 tests passed. Covers exact nine-tranche issuance and fixed cap, 80%/20% reward splitting, signed actions and replay protection, referral and computation limits, grant uniqueness/locking, staking/unbonding, quorum/timing, weekly awards and ledger reopening.
- The signed HTTP workflow builds actual PoW over a small synthetic dataset, qualifies and bonds a validator, mines for a different wallet, signs an attestation and settles a block using an advanced test clock. It verifies candidate status before/after settlement. It does not spend live startup allocations.
- Route tests include wallets, validators, community, economics, candidate records and both English/Chinese whitepaper downloads.
- Release build, `cargo fmt --check` and strict Clippy passed.
- `node tests/wallet_crypto.mjs`: encrypted backup recovery, wrong-password rejection, Ed25519 signature verification and tampered-identity rejection passed with ephemeral keys and fake browser storage.
- `node tests/validator_ui.mjs`: an in-flight and completed recomputation survives periodic refresh, vote updates and a language switch; duplicate UI attestation is prevented and wallet changes discard prior verification state.
- Native JavaScript syntax checks passed. English/Chinese dictionaries contain 936 matching string keys.
- Two Python conversion tests passed, including official-source enforcement and preservation of existing output.

## Browser checks

- English homepage renders the locally vendored Three.js brain. The visualization uses 24,000 spatial samples from official brain/optic ROIs, not a procedural whole-fly model.
- Language switching and navigation persistence were checked. Wallet, community, validator and economics views display translated controls and live local-ledger values.
- The community page displays real qualified points, the existing founding award and invitation link. Twitter follow/share buttons remain disabled and explicitly uncredited.
- The economics view shows all nine stages, 10,080 first-stage blocks, 3,093.58376 displayed initial subsidy, and the 30%-in-seven-target-weeks warning.
- Full-data diagnostic mining produced work hash `0012a766309d140aa6057aa4dffd3182d442ecabe77f9b9127df77c2f9aa4a58`; the 3D projection showed 100/2,000 winners and the proof passed all 11 recomputation checks. The activity is an algorithmic display projection, not biological firing.
- Monetary browser actions are not part of this QA. Existing user account, grant and candidate records are preserved; no live treasury reset or testing allocation is required.

## Final service restart

The rebuilt service restarted successfully. Full data/index revalidation took 83.40 seconds and returned `ready: true` with 311,833,243 records and a 2,742,389,584-byte compact index. Replaying the saved diagnostic proof again passed all 11 checks.

The pre-/post-restart snapshots matched: network ID, account count, existing account nonce/balance/stake/locked grant, remaining community reserve, chain height and ten pending candidates were unchanged. The service was left running. All ten page routes, both v0.2 whitepaper downloads, the chain endpoint and diagnostic candidate-state endpoint responded successfully.

## Limits of these checks

Wallet-signed votes follow server recomputation. They are not independent validator-node execution or Byzantine-resilient P2P consensus. Social identity and public Sybil review, adaptive difficulty, a fee market, cross-node data availability, full-index succinct proofs and scientific retrieval benchmarks are not implemented by these checks.

The current monetary rule halves stage-average subsidy after another 31,183,324.30 FLY has been mined. At continuous one-minute production, first halving is approximately one week after launch. Missing work/quorum delays it; the ledger never issues empty calendar subsidies. All stages total exactly 280,649,918.70 FLY, with the 31,183,324.30 FLY community reserve accounted separately.
