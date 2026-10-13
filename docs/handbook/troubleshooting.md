# Troubleshooting

Use the narrowest recovery step that fits the failed stage. Preserve the full model cache, saved results and public identifiers while investigating. A graphics fault, storage fault and RPC fault have different causes.

## Preparation does not advance

Check whether the active phase is download, integrity check or model construction. Record transferred bytes, the resource/digest named in the log, browser version and available storage. Check connectivity and retry the affected resource rather than starting another complete download immediately.

If there is a quota error, stop adding work and preserve/export available records. Private browsing or a different browser profile may not expose the previous cache. A completed download does not imply the model construction phase has finished.

## Mining says it is waiting

The initial Devnet plan is complete. Waiting for another calibrated task and finite budget is expected; there is no remaining paid unit in the old plan. A wallet signature or deposit cannot reopen it.

**Model ready** describes local preparation. **No open task** describes the authority's supply. Both can be true at the same time. Select **Check for new tasks** to refresh availability. Until a task is admitted, **Not running** is the honest local rate and no candidate should be counted as attempted computation.

For an admitted future task, check model readiness, wallet sign-in, grant validity, selected account/generation and the actual frozen unit. Do not reuse a solved task ID or treat partial work as completed.

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
