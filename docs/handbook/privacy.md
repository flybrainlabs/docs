# Privacy and security

The website separates public documentation and evidence from private candidates, customer requests and authorization material. Browser-local persistence and server-side archives are also separate storage domains. Read the site's [Privacy notice](/privacy/) and [Terms](/terms/) for the applicable user-facing policies.

## Public information

Documentation, atlas annotations and authorized result packages are public. Explorer exposes a public projection of rounds, candidates, verification and applicable wallet/unit/payment evidence. Solana public accounts and transaction signatures are observable on their cluster.

A public wallet address is not anonymous once connected to published activity. Publication of scientific material still requires its explicit authorization; a public financial receipt does not authorize publishing private input content.

## Private information

Private candidate bytes, salts, archive paths, customer tickets, signing keys and session credentials stay outside the public projection. Customer request access uses a private receipt token and authorized operations. Possession of that token can confer access, so protect it.

Private low-entropy inputs need appropriate salted commitments rather than a public bare hash that can be guessed. Confidential computation requires actual isolation and access control, not merely a private-looking UI.

## Browser permissions and storage

The browser retains verified model chunks, results and snapshots within the site origin/profile. Clearing site data can remove recoverable work; it is not a general-purpose fix for rendering or network faults. Export records deliberately when you want an additional portable copy.

Wallet Standard exposes public accounts and prompts for supported sign-in/transaction actions. The site does not require a recovery phrase or wallet private key. Scoped nonextractable session keys and origin-bound sign-in limit browser authorization; an on-chain grant separately bounds permitted rent consumption.

## Finite authorization

Review the account, cluster, program, expiry, per-result/cumulative limits and result count before a grant transaction. There is no automatic top-up or unrestricted beneficiary change. Revoke/withdrawal and applicable renewal need their actual wallet authority.

CSRF, one-use challenges, exact origin binding and wallet-generation isolation protect supported writes. They do not eliminate program upgrade trust, device compromise or unperformed extension-wallet acceptance.

## Requests, retention and disclosure

Request fields are removed after at most 365 days under the documented request policy. Audit/contract retention is separately disclosed. Deliverables, public sponsorship and publication choices should be stated in the scope and agreement before work starts.

Never include keys, wallet backups, credentials, customer data or private signed journals in repositories, exported public builds or support messages. Use public identifiers for outcome questions and the private ticket path for customer-specific follow-up.

## Documentation search

Handbook search downloads a static public text index and filters it in your browser. Search queries are not submitted to the mining authority or a third-party search provider by this feature. Opening a document does not start mining, grant funding, historical uploads or settlement.
