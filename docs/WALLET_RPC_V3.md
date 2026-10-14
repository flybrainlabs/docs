# Private RPC transport for wallet mining V3

## Current deployment boundary

The reported browser console contains HTTP 429 responses from the public Solana
Devnet RPC. Those responses prevent a fresh chain read used by mining admission.
They do not establish that the scientific authority stopped, that an old claim
exists, or that a transaction failed on chain.

The maintained sources now support an authenticated gateway backed by a private
provider endpoint, including Helius. **Provider activation is pending:** the
requested credential is not available in the current private configuration.
The live mining modules remain on `mining-start-20261013-v1` and their existing
public RPC until the private endpoint is supplied, verified and deployed. Passing fixtures
does not establish that an actual provider key works.

## Transport and chain identity

The website receives a credential-free URL at the existing wallet gateway:

```text
https://<configured-wallet-gateway>/api/mining/v3/rpc
```

The browser configuration retains the same schema, Solana Devnet genesis,
program, mint, policy, stage, frozen units and finite permission defaults.
Its `rpc` field selects the gateway. The provider URL lives only in the private
runtime's `rpcUpstream` field, excluded from the public configuration response
and rejected by the static exporter if found in browser configuration.

The gateway verifies the actual upstream genesis before use and periodically
checks it again. The browser independently checks the returned genesis before
admission, grant submission and candidate acceptance. A provider hostname alone
does not prove Devnet identity. Mainnet remains closed.

## Requests and recovery

The gateway requires an existing wallet login, the approved website origin and
the matching CSRF value for every POST. It supports bounded rent/account reads,
signature observations and block-height reads. It rejects batches, arbitrary RPC
methods, user-selected upstream URLs and oversized responses.

An authenticated miner may submit only a fully signed grant transaction whose
message matches that wallet's server-prepared request. The fee payer, program,
instruction count, signatures and packet size are checked. The gateway records
the original signature before forwarding. Arbitrary transfers and unreviewed
messages are rejected. No project signing key is used by the RPC route.

Four concurrent browser RPC calls, 80 requests per wallet per minute and 240
total requests per minute bound this route. Provider redirects and URL-bearing
error details are not forwarded. Temporary failure or HTTP 429 receives a
structured, readable retry instruction; the SDK's exponential rate-limit retry
is disabled for this connection.

Before Worker dispatch, a transport fault retains the selected candidate and
its input at the front of the existing resume queue. Explicit retry must retain
its original funding scope. A failed or zero rent quote cannot admit computation.
No model cache or result archive is cleared to recover RPC access.

Grant confirmation uses finalized HTTP signature observations. It does not
require a public WebSocket endpoint. Timeout or blockhash expiry leaves the
original transaction unconfirmed and does not authorize a replacement payment.
Device session keys are retained before a potentially ambiguous broadcast;
their private material remains nonextractable in the existing IndexedDB scope.
Extensions that offer only their own sign-and-send operation can still use an
extension-selected broadcast transport; the website cannot override that
provider choice. Its subsequent chain reads use the configured gateway.

## Activation procedure

1. Supply the provider's Devnet HTTPS URL through private configuration. Store
   it in a mode-0600 file with a `rpcUpstream` property, outside every repository,
   static export and command-line argument containing a credential.
2. Assemble and validate the pinned sources. Install the changed wallet service
   and its RPC module without replacing the authority, verifier, database, WAL,
   signer or archives. Preserve a private backup of both existing modules.
3. Run `infra/tools/configure_wallet_rpc_v3.py --private-rpc-file <private-file>`
   on the node. Its read-only probes require the pinned Devnet genesis and a
   positive current 1024-byte rent quote. It backs up the exact private runtime,
   changes only transport fields and skips an identical configuration.
4. Restart only the wallet gateway and check its health and public configuration.
   Restarting the gateway does not discard durable login/session records. Compare
   the frozen stage, units and permission defaults with the prechange baseline.
5. Set the website's `rpc` field to the approved gateway URL and rebuild the
   retained export. The maintained release builder updates that asset and CSP
   together. Deploy only verified changes with the existing backup/hash tooling.
6. Verify the real upstream chain and public asset hashes, then test authenticated
   browser reads. Real extension confirmation and full mining on the participant's
   device require separate evidence. Do not consume the existing finite reward
   units merely to repeat an operator acceptance run.

The configuration helper performs no signing or broadcasting. A configuration
change does not mint tokens, open a new budget or execute a reward payout.

## Verification

The transport and gateway suites passed 24 and 41 checks respectively. Four
configuration tests checked probes, exact frozen-field preservation, private
permissions, atomic backup, dry-run and idempotency. Two CSP tests checked the
legacy endpoint, gateway origin and rejection of credentials/unpinned networks.
Ten Chromium checks used the real bundled SDK with an isolated Wallet Standard
and RPC fixture, including a single-attempt HTTP 429. The wallet challenge suite
passed 15 checks using actual scripted Ed25519 signatures. No real provider,
extension confirmation, chain broadcast or physical-device acceptance is claimed.
