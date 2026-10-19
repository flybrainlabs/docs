# Continuous factory pool operations

## Scope and deployment status

The pool uses multiple unmodified V4 factories. Each catalog is sealed before
discovery. Existing task deadlines, scientific markers, beneficiaries and FBW
accounting remain authoritative. Browser work changes catalogs only at a safe
boundary. Previously saved candidates keep their original OPFS paths and reader.

The source implementation is opt-in. Publishing it does not activate the node,
fund a catalog, change the public deployment configuration, or establish native
model throughput. The example runtime is deliberately disabled. The original
node's private runtime remains unreadable to the current maintenance account;
installation requires its existing authorized administrator. Do not elevate or
try another identity to read that configuration.

## Components

- `factory_pool_queue_v4.mjs` uses PostgreSQL server-time leases, row locks with
  `SKIP LOCKED`, monotonic fencing and immutable job/transaction identities.
- `factory_pool_supply_v4.mjs` imports an approved finite plan, reserves unique
  science in one database transaction and registers the exact compiled catalog.
  Existing on-chain science markers are checked before reserving chain funds.
- `factory_pool_calibration_v4.mjs` runs only the exact approved generator hash.
  It preregisters an inventory containing at least all 55 previously known goals,
  including the 16 retained reserve goals. Later generations also include every
  prepared catalog. A fixed scientific envelope and a finite aggregate reward
  authorization constrain automatically approved generation output.
- `factory_pool_service_v4.mjs` maintains separate catalog contexts, authenticated
  input assignments, persistent replay jobs, valid-candidate finalization and
  fixed-entitlement payments. Each admitted signer executes its own full replay.
  Two keys under one operator remain one operator.
- The browser verifies authority signatures, the pinned pool scope, finalized
  factory accounts and the scientific envelope. All adapters share a wallet send
  queue. Pool payment consent lasts only while the wallet is unlocked.

Input leases reduce simultaneous duplicate computation. They are advisory and
never establish scientific acceptance or a reward. Renewals are tied to the
authenticated wallet and page session. Finishing releases the input; a stopped
client's lease expires. An unverified client cannot permanently mark an input
scientifically completed. The chain still decides which valid solution wins.

SSE events are discovery hints. The durable event cursor permits reconnection;
clients continue to verify the signed manifest and personal-RPC chain state.

## Prepare and verify a source bundle

Run from the assembled workspace:

```sh
python3 tools/prepare_factory_pool_v4.py \
  --workspace /path/to/assembled-workspace \
  --output /path/to/new-private-stage
```

The manifest hashes every source file and the complete archive. It includes no
model, private runtime, keys, DSN, signed operator transactions or scientific
event archives. Install dependencies from the pinned package lock in a separate
release. PostgreSQL requires the pinned `pg` driver; SQLite remains in use for
the retained upload archive. Initialization adds the dedicated PostgreSQL schema
under an advisory migration lock and does not migrate existing SQLite data.

## Administrator activation gate

Before changing the original service, prepare a coherent SQLite backup and a
PostgreSQL backup, retain its source symlink, and record the original health and
service state. Keep the original model/cache and all archives in place.

Fill a private copy of `factory-pool-v4.example.json` using the existing approved
runtime and identities. Use a dedicated PostgreSQL database/role. Put its DSN in
the private file referenced by `databaseUrlFile`. Do not place it in the public
deployment or a command line.

The public trust object has schema `flybrainlabs-factory-pool-trust-v4` and binds
`poolId`, `authority`, `genesisHash`, `programId`, `mint`, `policyHash`,
`anchorFactory` and `envelopeHash`. Its `envelope` fixes graph, model, parameter
profile, input domain, evaluator, steps, timestep and candidate/stimulus bounds.
The envelope hash is SHA-256 of protocol canonical JSON. Verify its authority
against the retained anchor's finalized account before publishing it.

`supplyAuthorization` requires the approved evidence hash and aggregate
`rewardAtoms`. Every imported catalog counts against that authorization; no
minting or automatic funding is available. Calibration additionally requires
the matching evidence hash, `python`, exact `tool`/`toolSha256`,
`initialInventory`, `outputDirectory`, `groups`, `deadlineSeconds` and exact
frozen `rules`. Keep the generator's retained complete-model/cache workspace.
The calibration source does not download a model.

Configure `capacityObservations` from actual measurements:
`peakTasksPerSecond`, `prepareP95Seconds`, `registrationP95Seconds`,
`safetyFactor`, `minimum`, and `maximum`. The target is consumption times total
preparation latency times the safety factor, with explicit lower/upper bounds.
An observation requiring more than the configured maximum is reported as a
capacity shortfall. Replay or disk pressure stops further publication.
`minimumOpenCatalogs` separately keeps immediately usable or ready-to-open
catalogs available. A queued future task behind a closed claim window does not
satisfy that requirement. Preparation/registration latency also determines when
a still-open catalog loses sufficient runway and replenishment should start.

Start the new service on a temporary loopback port first. Verify its database,
native model readiness, signed manifest, content, CORS, personal-RPC browser
flow and all pending old submissions. Select replay concurrency only after
measuring complete replay CPU, memory and disk usage on that host. The existing
service's 512 MiB cgroup limit and CPU quota require review for additional native
processes. Queue-only load tests cannot establish native replay capacity.
Size the retained archive from actual disk and expected result volume. The
legacy 2 GiB configuration ceiling remains the default. An explicit
`poolStorageApproved` runtime permits a finite allocation up to 1 TiB, while
the configured disk reserve and shared SQLite byte reservations still apply.
This does not allocate storage, buy a service, delete archives or prove host
capacity. Verification pressure defers new input assignments before more CPU
work starts; existing assignments can still renew and finish.

After successful maintenance acceptance, switch the original proxy/service to
the tested release, and publish the pinned `taskPool` trust and manifest URL in
the website deployment. Returning users explicitly approve the pool payment
scope after unlocking. Preserve the original service for rollback. No contract
upgrade, mainnet activation, main merge or model download is required.

## Financial recovery and backpressure

Signed packets are committed before broadcast. A retry reuses those exact bytes.
Expired unknown transactions block their job; no replacement debit is invented.
Reconcile the original signature and business account through finalized reads
before any administrator recovery. Never edit or delete signed packet rows.
Proof of an already completed operation prevents another send even if the RPC
cannot retrieve its original receipt.

Review blocked jobs and queue depth before admitting additional catalogs.
Preserve accepted unpaid rewards. Finalize an eligible valid candidate before
expiry/retry, including when an earlier commitment has just lost eligibility.
Current winning-solution rules do not promise a reward for every miner.

## Acceptance commands

```sh
node tests/factory_pool_v4.mjs
FLYBRAIN_POOL_TEST_SOCKET=/var/tmp/flybrainlabs-postgres-acceptance-YYYYMMDD/socket \
  node tests/factory_pool_queue_v4.mjs
FLYBRAIN_POOL_TEST_SOCKET=/var/tmp/flybrainlabs-postgres-acceptance-YYYYMMDD/socket \
  node tests/factory_pool_sbf_v4.mjs
```

Use the dedicated unprivileged PostgreSQL acceptance instance on its Unix
socket. The SBF test creates a separate acceptance database per VM and retains
its evidence. It combines actual PostgreSQL and actual SBF/SPL execution with
explicit native-replay fixtures. Real science, personal RPC, target-scale native
throughput and original-node activation require their own evidence.
