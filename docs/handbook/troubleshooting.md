# Troubleshooting

Use the narrowest recovery step that fits the failed stage. Preserve the full model cache, saved results and public identifiers while investigating. A graphics fault, storage fault and RPC fault have different causes.

## Preparation does not advance

Check whether the active phase is download, integrity check or model construction. Record transferred bytes, the resource/digest named in the log, browser version and available storage. Check connectivity and retry the affected resource rather than starting another complete download immediately.

If there is a quota error, stop adding work and preserve/export available records. Private browsing or a different browser profile may not expose the previous cache. A completed download does not imply the model construction phase has finished.

## Mining says it is waiting

The initial Devnet acceptance plan is complete. Task-supply revision 3 now opens two new calibrated targets under a separate two-FBW stage. Refresh once to load the current deployment and budget. The selected provider's existing permission and the model cache are retained. If an already open page detects a stage change, the client checks the published budget against the live gateway while keeping its pinned asset, roles and permission defaults.

Check the authority's actual task state before diagnosing an empty queue as a network fault. If it reports exhausted supply with no open round, another prospectively calibrated and funded plan is required. A wallet signature or deposit cannot reopen a paid unit.

**Model ready** describes local preparation. **No open task** describes the authority's supply. Both can be true at the same time. Select **Check for new tasks** to refresh availability. Until a task is admitted, **Not running** is the honest local rate and no candidate should be counted as attempted computation.

For an admitted future task, check model readiness, wallet sign-in, grant validity, selected account/generation and the actual frozen unit. Do not reuse a solved task ID or treat partial work as completed.

## The model is prepared, but no worker is computing

**Requested 1 · prepared 1 · computing 0** means one worker has loaded the model. It does not establish that the wallet has permission to start a candidate. An open target and an idle prepared worker can coexist.

The main control now names the next admission step. Connection, login, scientific task availability and finite rent authorization are checked separately:

| Visible state or action | Meaning | Next step |
| --- | --- | --- |
| **Sign in** | The connected wallet has no current site login. | Review the sign-in message. |
| **Check wallet state** | Balances and grants have not synchronized. | Retry the wallet read; no compute or transfer is triggered. |
| **Review rent grant** | No usable grant exists, or its remaining credit or per-result limit is insufficient. | Review the finite limits and explicitly confirm a create/renew operation if you want to proceed. |
| **Renew device authorization** | A grant exists, but its nonextractable signing key is unavailable on this browser/device. | Explicitly renew on this device; connection restoration does not restore a grant key from another device. |
| **Check for new tasks** with a funding message | This round has no usable frozen reward unit. | Check the published plan and current gateway state. A deposit cannot supply a missing reward budget. |
| **Start mining** | The visible admission checks permit a start attempt. | Select it; the client rechecks live funding, actual rent and the device key before any worker dispatch. |

Opening a review does not sign a transaction, change a grant or start the CPU. Canceling leaves the prepared model and saved artifacts intact. A successful grant review also does not start computation automatically; select **Start mining** when ready.

If another failure appears, expand **Technical diagnostics** and report its exact text, the time and the visible wallet state. Network, browser storage, model-lock and funding errors retain distinct explanations. A generic error alone cannot identify the cause. Cached public addresses, local preparation and a task lookup returning 404 are not evidence of wallet authorization or active computation.

## A claim lookup returns 404

The claim endpoint reads an existing submission; it does not provide a new task. A response with `NOT_FOUND: claim` means that particular claim was not found by the responding authority. Check the signed current-round and readiness responses to establish service health and task supply separately.

A browser can retain a candidate and its calculated claim ID before the server accepts the commitment. When the signed round is closed, the deadline has passed and no acceptance receipt exists, the website marks a missing claim as **Round closed · candidate not admitted; results retained**. It stops automatically polling that candidate while keeping its identity, metrics and downloadable outputs. A missing receipted claim, an open round or a transport error still requires reconciliation; these cases are not treated as completed submissions.

## 3D is blank or slow

Use graphics retry or disable graphics while retaining computation controls. Compare the normal [Neuron atlas](/atlas/) as a structural control and record whether WebGL is available. Check the display-resource error before touching scientific model storage.

Reduce worker concurrency if the device becomes unresponsive, and record the setting. Public simulated/mobile layout checks do not establish that your physical Android/GPU combination has passed acceptance.

## Wallet connects but cannot proceed

Connection, sign-in and grant are different states. Confirm the selected account, challenge origin/chain and whether sign-in expired. Reject an unexpected message or transaction. Read the finite grant review and plan state.

An account switch creates a new authorization context. Prior accepted settlement stays with the original wallet. Inspect its account-specific history rather than expecting the new wallet to receive that reward.

## The page asks for the wallet again after refreshing

The site now restores the selected wallet's existing permission silently. If restoration is unavailable, unlock the extension, confirm it supports Wallet Standard on Solana Devnet and reconnect once. Keep the same browser profile and permit this site's storage. An expired site login asks for sign-in rather than another wallet selection. Explicit sign-out intentionally stops automatic restoration.

Temporary node errors can delay balance synchronization without discarding a valid connection or login. They do not prove that a deposit or grant failed. A saved public address is never displayed as an authorized connection when the wallet did not confirm it.

## A transaction is unknown

Keep the original public signature, business/unit ID and beneficiary. Retry reading trusted evidence. RPC timeout, missing history or blockhash expiry alone cannot prove failure. Durable reconciliation must determine whether the original action executed before another financial attempt.

A closed temporary Result can coexist with a permanent paid unit. The documented close case paid no duplicate reward or rent. Use [Explorer guide](/docs/explorer/) to follow the permanent evidence.

## A result appears in one place but not another

Local history, private accepted candidates, authorized public publications and the public projection have different scopes. A local save is not server acceptance; a private claim is not automatic public publication. The projection may also lag.

Compare IDs and visible states. Use the result center for authorized reproduction packages and Explorer for competition/payment evidence. Do not upload private salts or ticket credentials to explain the difference.

## Send a useful report

Use [Contact and requests](/services/request/). Include the action, active phase, exact visible error, browser/device, time, public task/candidate/signature and whether the error repeats after a targeted retry. A screenshot can illustrate layout; pair it with the readable error text.

Exclude wallet backups, private keys, signed session material, customer inputs and private receipt tokens from public reports. Keep recovery steps explicit so they do not accidentally repeat completed payments or issuance.
