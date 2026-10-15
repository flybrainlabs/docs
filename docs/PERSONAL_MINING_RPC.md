# Personal mining RPC

The official mining page provides **RPC settings** in the left mining console.
Release `contract-factory-v4-20261015-r5` supports personal Helius connections
to Solana Devnet. Wallet connection is not required to configure the RPC.

## Configure Helius

1. Open **RPC settings** on <https://flybrain.work/mining/>.
2. Follow **Register with Helius for free** to
   <https://dashboard.helius.dev/signup?plan=free>.
3. Create an API key in the Helius dashboard, select **Solana Devnet** and copy
   the complete HTTPS RPC URL, including its `api-key` query parameter.
4. Paste it into the masked URL field and choose **Check and use**.

Helius lists a free plan at <https://www.helius.dev/pricing>. Registration and
free-plan availability were checked on 2026-10-15; quotas remain subject to the
provider's dashboard. No subscription or API key is created by flybrainwork.

Before switching, the browser checks the exact Devnet genesis and the frozen
factory, catalog, policy and account owner. A wrong network, unrelated contract,
invalid key or unavailable connection cannot replace the current RPC. Buttons
remain disabled while the connection check and state refresh run.

## Storage and privacy

The default preference lasts for the current browser tab and survives its
reloads. **Remember in this browser** explicitly stores the URL on the device.
Saved endpoints are revalidated after reload; unavailable saved connections
fall back to the default while retaining the preference for repair.

The URL stays in the user's browser. Chain queries and wallet-signed transaction
broadcasts go directly to Helius; project session, CSRF and cookie credentials
are stripped. Content uploads retain their original authenticated project route
and do not receive the personal RPC URL. The field is masked by default, with
an explicit Show/Hide control. Diagnostics exclude the URL and API key.

**Use default RPC** removes only this preference. It retains wallets, complete
model caches, saved results, signatures and submission recovery state. Changing
the connection does not start a new mining session or create a reward budget.

Requests share one browser lane with a 250-ms minimum gap, at most 16 pending
requests and at least 1,100 ms between broadcasts. This bounds RPC pressure;
successful-task progression remains controlled by the contract.

## Scope and verification

Personal RPC settings affect this browser's chain reads and broadcasts. The
verification node has a separate operator-configured upstream; this UI does not
give users access to its runtime configuration or change its validator identities.
The existing finite catalog still pays 200 FBW per contract-confirmed winner.

Six SDK groups and six checks each on the staged and actual official website
passed. The browser checks exercise real CSP/CORS, invalid-network rejection,
masked input, duplicate-click prevention, tab and opt-in persistence, reload
revalidation, reset and desktop/390px layouts in English and Chinese. Model
caches and all six retained candidate records survived. No model download,
wallet signature, transaction broadcast or additional budget was used.

Provider responses in those UI tests are explicit public-account fixtures; no
real Helius API key was supplied. Actual private-provider acceptance therefore
requires a user's valid endpoint. Evidence is the infrastructure
`docs/PERSONAL_MINING_RPC_V4_ACCEPTANCE.json`. Separate real Devnet complete-model
payments and original-node restart evidence are recorded in
`TASK_FACTORY_V4_LIVE_ACCEPTANCE.json`.
