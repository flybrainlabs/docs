# Wallet connection and sign-in

The website uses Wallet Standard for the new Solana mining experience. The wallet entry appears in the header, while mining and account pages show the relevant grant and history controls. Public reading does not require a wallet signature. The primary mining entry starts with wallet connection and sign-in; it never starts computation merely by opening the wallet selector.

## Three separate states

| State | What it establishes | What it does not authorize |
| --- | --- | --- |
| Connected | The wallet exposes the selected public account | A deposit, grant or arbitrary transaction |
| Signed in | A one-use message proves account control to the site's session | Unlimited financial authority |
| Grant active | An approved on-chain grant permits narrowly bounded actions | Unlimited rent, beneficiary changes or automatic top-ups |

A connected account can still need sign-in. A signed-in wallet can still have no valid grant. An active grant can still encounter a completed plan or an exhausted result-count limit.

## Reloading and restoring the connection

After a successful connection, this browser remembers the selected wallet's name and public account, scoped to the test network and program. Reloading or navigating to another page asks that wallet to restore its existing connection silently. The site confirms the account supplied by the wallet before showing it as connected; a saved address alone is not a connection.

An unexpired site login is retained in the same tab and checked against that account. Connection restoration does not request a signature, create a grant, deposit SOL or restart mining. If the login has expired, the wallet can remain connected while the site asks you to sign in again.

If the wallet is locked, missing or no longer permits silent connection, unlock it and select **Connect wallet**. Late wallet registration can complete restoration without another selection. Selecting **Sign out / disconnect** clears the remembered connection and this tab's login, so the next refresh stays disconnected. An account change invalidates the old connection and keeps accepted rewards with their original beneficiary.

Only the wallet name and public account preference go into local storage. The existing short-lived login stays in tab session storage; wallet keys and grant signing keys are not copied there. If browser settings block storage or a different browser profile is used, restoration may be unavailable. These conditions do not remove the saved scientific model or results.

## Sign-in message

The server generates a one-use SIWS challenge. The message binds the account, origin, URI and chain. Review it in the wallet before signing. A challenge that has expired or already been consumed must be replaced; changing a visible label cannot make it valid again.

The browser also uses scoped session authorization. The session key is nonextractable through the supported browser crypto path, and it is bound to the relevant wallet generation. It does not expose the wallet's private key to the website.

## Before approving a transaction

Read the selected account, Solana cluster, program, grant limits and deposit amount. A sign-in signature and a transaction approval are different interactions. The transaction review should match the public plan and [FBW Devnet reference](/docs/devnet/).

Do not use a symbol alone to recognize an asset. The current token is the pinned FBW Devnet mint; a different mint with the same name is a different asset.

## Switching accounts and generations

Account changes isolate future asynchronous actions and history views. A response created for an old wallet/generation must not fund or alter the newly selected wallet. Existing accepted settlement remains tied to its original beneficiary.

Switching wallets therefore does not redirect a reward already accepted for another wallet. Reconnect and complete the appropriate sign-in for the intended account. Check the account-specific history when a prior action appears absent from the current view.

## My records and local history

Open [My records and payment settings](/account/) to review account-scoped work, accepted contributions, wallet-mining grant/history and applicable asset evidence. The local calculation link opens retained browser contribution records; it does not automatically upload them.

Local calculation, accepted contribution and settled assets have different evidence. An address ownership binding does not migrate historical beneficiaries or create a second entitlement. Read a prior record under its original identity when reconciling a wallet change.

## Compatibility and acceptance

The old local `fly1` keystore is isolated from the new wallet flow. It is not silently imported as a Solana wallet or used to authorize Devnet funding.

Actual Chromium checks with a mock Wallet Standard provider and public Devnet scripted signing have passed. Real extension-wallet confirmation remains pending. If your extension does not expose the necessary standard features, report its name/version and the visible failure rather than assuming a browser test certified that extension.

See [Grants, rent and refunds](/docs/grants/) for what a grant can spend, and [Privacy and security](/docs/privacy/) for the separation of public accounts and private credentials.
