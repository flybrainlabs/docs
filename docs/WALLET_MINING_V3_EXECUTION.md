# Wallet mining V3 execution

## Input and verified starting point

The owner supplied `flybrainlabs_wallet_mining_codex_prompt.txt`: 36,633 bytes,
253 lines, SHA256
`dbaf5df05f10d06aeb7edaa25bbc200e8c1a3ffb4bd77ebf20f48aa7168a7f31`.
The entire attachment was read. It authorizes the required non-mainnet code,
program deployment, finite test plan and acceptance transactions. No mainnet
asset or production payment is authorized.

The existing FBW asset is the only proposed asset for this test:

- Network: Solana Devnet.
- Genesis: `EtWTRABZaYq6iMfeYKouRu166VU2xqa1wcaWoxPkrZBG`.
- Mint: `HCdV49RkqtC7pPwzHCYg5KtkmU8opifjojLbAyZXKgQW`.
- Name: `flybrainwork`; symbol: `FBW`; precision: 8.
- Initial issuance: 31,183,324,300,000,000 atoms, with the exact V2 three-pool
  allocation. Both creation/issuance transactions are finalized. Mint authority
  is revoked and freeze authority is absent. Do not issue a second token supply.
- Current pool custody and public receipts: `contracts/deploy/fbw-devnet.json`.
  The supplied wallet controls the three initial token accounts. Wallet/mint/
  account key material and signed journals are external private files.
- Project/GitHub identity remains `flybrainlabs`; `web` is private. The supplied
  logo release is live and passed 42 local and 42 public layout checks.

The live scientific authority was queried before changes. It reports
`RESEARCH_STAGE_COMPLETE`, 29 rounds, 27 solved goals, zero pending/deferred
or unopened goals, and 2,345,991,272 reserved private archive bytes under a
4,294,967,296-byte declared cap. Do not silently reopen solved goals or award
historical unbudgeted results. New acceptance goals need distinct scientific
identities, real full-model calibration and prospective budget publication.

## Implementation state

The contract and gateway passed public Devnet complete-model acceptance.
The website release and its public acceptance are recorded below. This is a
finite test plan, not formal emission or production funding.

The first prerequisite changes distinguish structured native `VALID` and
`INVALID_RESULT` from `LOCAL_MODEL_ERROR` and `RETRYABLE_INFRA_ERROR`; all required
backgrounds must actually replay before any scientific vote. Lease admission
checks the particular frozen job's graph, model, parameter profile and evaluator.
Infrastructure faults are fenced, persisted and retried without a scientific
negative vote. Original result bytes and scientific signature domains stay intact.

Burn recovery now distinguishes the original CAP issuance proof from a smaller
current supply. Global issuance/authority and actual vault identity checks remain.
Explorer recovery updates sequence/date columns, keeps trusted values on a later
fault and resumes the saved historical `before` cursor.

## Required chain architecture and invariants

Continue the V2 economic program with an explicitly versioned mining extension;
keep instruction tags 0-9, old account layouts and signature domains compatible.
The test deployment must adopt the existing FBW supply and its fixed pools,
retaining the actual upgrade authority. It must not call `Issue` again.

New logical discovery units use the permanent `slot-v2` economic seeds with a new
account discriminator/layout, so an old independent `Claim` cannot decode them.
Reserve a unit's amount and task before the winner is known. Candidate financial
intents live in separate program accounts; registering an intent cannot let an
early caller capture the reward slot. Two authorized economic certificates must
bind the final scientific winner, claim sequence, wallet, fixed unit amount,
model/result commitments, chain/program/policy and narrow session authorization.

Funded grants have native SOL principal, a distinct project-paid management rent,
fixed miner/reward wallet, session key, expiry, per-result/cumulative limits,
result-count limit and monotonic wallet generation. No arbitrary CPI, beneficiary
change, auto-topup or project withdrawal of unused principal is exposed. Renewal
and funding rebind need the original miner's transaction authorization and keep
the original claim, science, beneficiary, economic uniqueness and payable amount.

Project-funded sealed staging can carry the 1024-byte summary outside transaction
packet limits. Permanent unit/intent state retains signature acceptance and
payment facts. The final operation atomically validates authorization, debits
only actual missing result rent, allocates/writes exactly 1024 bytes, transfers
the frozen amount to the correct wallet ATA and marks the unit paid. The relayer
pays network fees and auxiliary accounts. A failure rolls back business effects;
network fees remain separately observable.

Project-only result closure needs its real signer, fixed rent destination,
retention/archival evidence and a paid unit. Permanent economic evidence is never
closed. Closing a result cannot permit repeat rent consumption or reward payment.

## Integration and required evidence

Implement server-generated one-use SIWS challenges and authenticated wallet
sessions with origin/URI/chain binding. Wallet connection, login and grant validity
are separate states. New Wallet Standard navigation isolates the old `fly1`
keystore/header. Financial async callbacks and histories are wallet/generation
scoped; already accepted settlement stays with its original beneficiary.

Persist financial intent, winner evidence, signed transaction transport/outbox,
unknown-state reconciliation and wallet-paginated round histories. Scientific
terminal status must not stop financial reconciliation. Only finalized result,
permanent payment and beneficiary-token evidence may display reward received.

Build and test permission, quota, expiry, revoke/renew/rebind, atomic rollback,
old-Claim bypass, replay/close, packet/CU, burn and unknown transport cases in an
actual SBF bank before public Devnet. Freeze a clearly test-only finite plan with
real complete-model acceptance goals. Demonstrate at least two different rewarded
units under one grant, one still-readable 1024-byte result and a dedicated close
case. Report local scripted signing, mocked wallet transport, actual extension
confirmation and physical device acceptance separately.

Program/grant/stage configuration, fees, role keys and deployment costs must be
recorded before funding activation. The final record must contain real public
addresses, signatures, decoded accounts, budget/allowance deltas, cross-component
commits and reproducible commands; it must never contain private key material.

## Final Devnet evidence

Public receipts are maintained in `contracts/deploy/wallet-mining-v3/`.
The existing buffer was resumed by comparing actual stored bytes, writing only
missing ranges and retaining the signed transport journal outside Git. The
286,616-byte deployed SBF matches SHA256
`a42cd5db781b2675ce60e6c215e0e60918114351f5733a8c041174a6f0069b7b`.
Program: `5yxjnH1PSk8iQKfK3ejG4jfSkewkTKfcpJygojdb6sam`.
ProgramData: `GmTNV9aBMjWeEEsZxBhRAFhahFu2ivUssy1MdHVXam64`.
The supplied project wallet retains upgrade and result-close authority.

The once-issued FBW supply was adopted, never issued again. Two prospective
complete MaleCNS targets were registered only after the two-FBW finite budget
and unit reservations were finalized. The scientific plan is revision 2, hash
`efe25394bb5544d5fadace48a561d07d46d0422d4e47c885beea748cb40be393`.
Both targets cold-start their calibration families; old success samples and
historical unbudgeted science do not acquire rewards.

| Project round | Frozen reward | Actual result rent | Finalized payment |
| --- | --- | --- | --- |
| 30 | 100,000,000 atoms / 1 FBW | 5,852,160 lamports | [transaction](https://explorer.solana.com/tx/2ayKE5iZWaPRSmZJ4R3JUHBJvfad7jbGe8VqcfvCp1c8EH2t3G5WyX7hKAy5rcHqzuuLaTUDchJcaSJnKqg7Dvby?cluster=devnet) |
| 31 | 100,000,000 atoms / 1 FBW | 5,852,160 lamports | [transaction](https://explorer.solana.com/tx/4EcBLHkHA5jTdBWp6TsAVVUMePzgNpx2WVaKjCsNfNXoET7KQ8FZEEVurrs93coi3LaJrqQX9vWPwkgYpEVYkmJU?cluster=devnet) |

One funded grant paid both units without another miner transaction signature for
candidate admission, scientific upload/reveal, economic certificates or payment.
The grant originally deposited 23,408,640 lamports, capped cumulative consumption
at 11,704,320, capped each result at the RPC quote and allowed two results.
The holder separately burned ten token atoms between payments. Both subsequent
payment and recovery succeeded; no mint authority was restored.

The first dedicated test Result was closed after retention, full archive
rechecking, two narrow authorized archive certificates and the real project
signature. Close transaction:
`4EMVqATJTynm28y79X49yasDAzEhtPRLVhVQHxYfyv3vqKFYA4o4refr2uCRJEEMRkq6FDbFTgBXdA5cuVoSHUG6`.
Its 5,852,160 lamports returned to the fixed project recipient, with a separate
5,000-lamport transaction fee. Actual finalized replay after closure recreated no
Result, consumed no additional rent and paid no duplicate token. The permanent
unit remains paid. The second Result remains directly readable at
`CUwx4EwnmCQQPpzE2Wkoy5qFL7xdcKJ4mBvFJz7PS8Rv`.

The miner explicitly revoked the grant and withdrew 11,704,320 unused lamports
to the same wallet. Withdrawal transaction:
`aq7Jn92ozH6QCaxcngNHUQTQY4u8njusGEanM5mQedU9DZjLrJsqqN2ATUhQwCoH88bjCjb8bK7H8QT7gRANKbt`.
This withdrawal returns unused principal; it does not reclaim consumed result rent.

## Verification and recovery

- Actual local SBF bank: 60 main and 11 boundary checks; maximum supported
  packet 1126 bytes, maximum measured CU 91733.
- Native replay: complete 165122-neuron, 256-step byte match; a separately
  corrupted response underwent fresh complete replay and returned
  `INVALID_RESULT`, never an infrastructure-derived scientific vote.
- Authority: 16 integration tests, including funded-claim admission and earliest
  eligible winner ordering. Existing campaign configuration and signed domains
  were retained; wallet tables and financial gates are additive.
- SIWS/origin/session/CSRF: 15 actual Ed25519 and HTTP checks.
- Durable transport: nine mocked-fault checks with real signed transaction bytes,
  retained outbox, coalesced requests, fenced leases and canonical Buffer recovery.
- Browser Wallet Standard: seven actual Chromium checks with mock wallet/RPC,
  including canonical grant review, nonextractable scoped session keys, wrong
  account rejection and stale-wallet callback isolation.
- Explorer recovery: 11 fault/cursor checks. Candidate pages link the actual
  wallet, permanent unit, grant consumption, 1024-byte Result and finalized
  transaction. Project closure updates retained historical evidence.
- Public Devnet: two fresh complete-model winners with all required backgrounds,
  authorized full native replays, exact finalized token deltas, burn recovery,
  project-only close and miner-only unused-principal withdrawal.

The original cloud upgrade backup was read back before installing the gateway
and native binaries. Counts of 38 historical claims, 27 winners, 75 artifacts and
27 planned goals matched exactly after the upgrade. Subsequent changes are the
prospectively registered acceptance work. Model files, SQLite/WAL, private
archives and all historical identities were preserved. Gateway restarts during
acceptance resumed the existing intents and transactions without another grant
or recomputing saved candidates.

The two-unit test plan is complete. No new deposits or paid units are admitted
under this exhausted plan. Preparing the model, wallet login, history and unused
principal withdrawal remain available. A future paid plan requires prospective
calibrated tasks and a separately frozen finite budget. Mainnet, formal emission,
production payments and Marketplace revenue flows remain unactivated.

Actual extension-wallet confirmation and physical-device/GPU acceptance have not
been performed. Scripted local signing, mock-wallet Chromium and public chain
acceptance are separately identified. Three signing identities on one node do
not establish independent operators.

## Reproduction commands

Run commands from the assembled workspace, using the component maps and pinned
infrastructure manifest. Key files and signed journals stay outside checkouts.
Inspect the existing public receipts and chain before invoking any transaction
command; completed issuance, initialization, payments and closes are not rerun.

```sh
node tests/wallet_login_v3.mjs
node tests/mining_transport_v3.mjs
node tests/replay_faults_v3.mjs
node tests/explorer_chain_faults.mjs
cargo test --offline --test target_authority
/usr/bin/python3 tests/wallet_browser_v3.py
```

The Devnet acceptance driver `tests/wallet_devnet_v3.mjs` restores its private
checkpoint and existing grant. `tests/wallet_v3_close_devnet.mjs` restores its
operator journals. These are scoped acceptance tools, not public arbitrary
transaction endpoints. See [the exact Result layout](WALLET_MINING_V3_RESULT_LAYOUT.md).

## Website acceptance

The wallet-mining V3 interface is published at `https://flybrain.work/mining/`
with a permanent Wallet Standard entry on home, mining, account and Explorer.
Local and public Chromium each passed 24 width/language/route checks at
320, 390 and 1440 pixels, in English and Chinese. Public layouts verified a
visible wallet entry, isolated legacy wallet header, no horizontal overflow,
finite-plan status and no automatic mining or authorization. They are simulated
viewports, not physical Android acceptance. The complete 11751-type atlas and
all retained scientific/cache paths are unchanged. Model preparation remains
usable when financial services are temporarily unavailable.

The release exposes only public chain and budget identity. It keeps legacy
formal chain configuration disabled, pins Devnet RPC/WSS in CSP, and displays
real finalized rewards separately from scientific success. The two-unit plan
is marked complete. Fresh paid tasks and deposits await another frozen plan;
accepted settlement/history and unused-principal withdrawal remain available.
