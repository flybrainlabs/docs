# Personal mining RPC

The official mining page requires **RPC settings** before model preparation and
mining. Release `contract-factory-v4-20261015-r6` accepts a Helius API key and
selects its RPC endpoint from the published deployment. The current deployment
uses Solana Devnet. Wallet connection remains available from the header.

## Configure Helius

1. Open <https://flybrain.work/mining/>. The required RPC setup opens automatically.
2. Follow **Register with Helius for free** to
   <https://dashboard.helius.dev/signup?plan=free>.
3. Create and copy an API key in the Helius dashboard.
4. Paste only the key into the masked **Helius API Key** field and choose
   **Verify and continue**.
5. Connect and sign in with the wallet, prepare the model and begin mining.

The browser constructs the Helius URL. Users enter neither a full RPC URL nor a
network selection. The endpoint follows the deployment's cluster and exact
genesis. The key cannot change the deployment or activate mainnet. A future
mainnet release still requires its separately authorized program, catalog,
wallet and funding configuration.

Helius lists a free plan at <https://www.helius.dev/pricing>. Registration and
free-plan availability were checked on 2026-10-15; quotas remain subject to the
provider's dashboard. No subscription or API key is created by flybrainwork.

Before enabling mining, the browser checks the deployed network's exact genesis
and the frozen factory, catalog, policy and account owner. Invalid keys,
wrong-chain replies and unrelated contracts leave mining blocked. Connection
checks show progress and coalesce repeated submissions.

## Required connection

Missing, removed or unsuccessfully restored keys block mining entry. The main
button opens RPC setup, and the browser makes no shared RPC requests. Personal
RPC failures never fall back to a project or public RPC. Configure or repair the
key and verify it again to continue. Removing or replacing a key pauses the
mining session, stops task polling and prevents queued broadcasts from using
an old connection. Already submitted transactions retain their original
receipts and recovery records.

The verification node keeps its independently configured upstream for replay
and settlement. Personal RPC settings control this browser's chain reads and
wallet-signed broadcasts. Content uploads and wallet login retain their
original authenticated project routes.

## Storage and privacy

The default preference lasts for the current browser tab and survives reloads.
**Remember the key in this browser** explicitly stores the key on the device.
Saved keys are revalidated after reload. Unavailable saved connections retain
their preference for repair and leave mining blocked. Existing full-URL
preferences are migrated to keys after successful network and contract checks,
using the same network-scoped storage key.

The key stays in the user's browser and is sent directly to Helius. Project
session, CSRF and cookie credentials are stripped from those requests. Content
uploads do not receive the personal key. The field is masked by default, with
an explicit Show/Hide control. Diagnostics exclude the URL and API key.

**Remove key** removes only this preference. It retains wallets, complete model
caches, saved results, signatures and submission recovery state. Changing the
connection does not start mining or create a reward budget.

Requests share one browser lane with a 250-ms minimum gap, at most 16 pending
requests and at least 1,100 ms between broadcasts. Contract task progression
keeps its existing rules. The finite catalog still pays 200 FBW per
contract-confirmed winner.

## Verification

SDK acceptance covers deployment-driven endpoint selection, missing-key gates,
wrong-chain and account identity rejection, duplicate prevention, session and
opt-in persistence, legacy preference migration, failed restoration, credential
isolation, removal and cancellation of queued requests. Browser acceptance also
checks mandatory setup, key-only input, reloads, provider outages and English /
Chinese layouts at desktop and 390px widths. It monitors both browser mining
RPC gateway routes to detect any shared fallback.

Provider responses are explicit public-account fixtures; no real Helius API key
was supplied. Actual private-provider acceptance requires a user's valid key.
The acceptance record is `infra/docs/PERSONAL_MINING_RPC_V4_ACCEPTANCE.json`.
Separate real Devnet complete-model payments and original-node restart evidence
remain recorded in `TASK_FACTORY_V4_LIVE_ACCEPTANCE.json`.
