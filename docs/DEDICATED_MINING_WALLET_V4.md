# Dedicated mining wallet for V4

## User flow

The mining page now requires a separate, user-owned wallet. It replaces repeated
extension confirmations for mining while retaining the existing factory,
scientific descriptors, FBW budget, model caches and saved candidates.

1. Create a twelve-word English BIP39 phrase on the device, or restore a dedicated
   mining wallet using twelve or twenty-four words.
2. Reveal and save the words offline, confirm three randomly selected words and
   set a local encryption password of at least twelve characters.
3. Verify a personal Helius API key. Network selection follows the deployment;
   the activated environment remains Solana Devnet and requires test SOL.
4. Transfer SOL to the displayed mining-wallet address. Review the live rent
   quote and explicitly enable automatic payments. There is no spending budget.
5. Prepare the retained model and select **Start mining**. An expired task is
   recovered under the frozen contract rules before computation begins. The
   local wallet signs permitted mining transactions and deducts their actual
   chain costs directly from its SOL balance.

Once explicitly started, a running, unpaused session automatically finalizes
valid candidates or expires eligible empty attempts and advances frozen tasks.
Idle pages, paused sessions, and single-round mode do not advance the catalog.
Queued sends check the active session before signing or sending. Unknown receipts
pause the session instead of blindly signing another recovery transaction.

Neither creating, unlocking nor funding a wallet starts computation. Reloading
locks the wallet and requires automatic payments to be enabled again. Approval
lasts only while the browser wallet is unlocked, with no monetary or four-hour
limit. Locking stops new signatures and sends; a transaction already
broadcast can still confirm. Existing ambiguous transaction receipts remain
available for reconciliation and are not blindly replaced.

## Ownership and cost explanation

SOL is transferred to the user's new wallet, rather than a project account or a
new rent-pool contract. New submission PDAs debit their payer directly through
the existing V4 instruction. There is no project surcharge for the rent deposit
or network transaction fee.

- A rent-exemption deposit remains in the Solana data account it funds. It is
  not a payment to the project team or to a company called Solana.
- Transaction fees are charged by the Solana network and are generally
  nonrefundable.
- Reclaiming an account deposit requires a supported close instruction. The
  frozen V4 submission accounts have no reclaim operation; the page does not
  promise refunds.
- Unused wallet SOL remains controlled by the phrase holder. A compatible Solana
  wallet can restore the same standard address to move the available balance.
- Actual rent is queried from the selected RPC. A VM's rent amount need not
  equal the current Devnet amount. The new-submission PDA quote is displayed;
  network fees and optional reward token-account rent are separate costs.
  Computation steps do not each create a PDA or consume that deposit.

## Header balances

On the mining page the top-right header shows finalized available SOL and FBW
from the same personal RPC used for task state. FBW reads the wallet's associated
token account for the frozen mint. Pending rewards are excluded; wallet balance
is not a claim of lifetime mining profit. Unknown balances display a dash, an
actual zero displays zero, and failed synchronization marks the retained data as
stale with a timestamp. Existing periodic refresh also updates reward receipts.
English/Chinese and compact navigation keep balances beside the wallet.

## Local secrets and signing scope

The standard derivation path is `m/44'/501'/0'/0'` using hardened SLIP-0010
Ed25519 derivation. The storage password encrypts the browser copy and does not
act as a BIP39 passphrase. The derived address is independently checked against
an existing Solana derivation implementation.

The browser uses BIP39 from `@scure/bip39`, HMAC/SHA-512 from `@noble/hashes`,
Ed25519 from `@noble/curves`, and the existing Solana transaction library.
The vault uses PBKDF2-SHA-256 with 310,000 iterations, independent random salts,
AES-256-GCM, a fresh nonce, and authenticated schema/address/path metadata.
Only ciphertext is saved in a separate versioned IndexedDB database. Switching
the selected encrypted wallet preserves previous records. JavaScript memory
cannot provide a guarantee of physical secret erasure; locking drops the active
signer and revokes its local authorization.

The local signer accepts the exact fresh site/network login challenge and
canonical instructions for this factory. It rejects arbitrary messages, SOL
transfers, administration, unrelated accounts/programs, changed beneficiaries,
excessive network fees, a wrong chain and unapproved spending. Associated token
account creation is limited to this wallet and the frozen mint. Replaying a
signed receipt reserves its cost before another send, with duplicate receipts
coalesced. There is no cumulative spending cap; insufficient SOL blocks a new
transaction. Program/account/beneficiary checks and the network fee sanity
ceiling remain enforced.

The phrase and local password are never passed to RPC, the project gateway,
Stitch, diagnostics or the Worker. A Worker receives a bounded MessagePort with
read access to the public factory and current task through the personal RPC.
It independently checks the frozen task representation without receiving an API
key, RPC URL or signing capability. No shared browser RPC fallback is enabled.

## Design reference and verification

Actual Stitch outputs were generated in project `5326488884783619575`:

| Screen | Resource |
| --- | --- |
| Desktop setup and funding | `d5abdb2253f148759410924d860baf12` |
| Mobile backup and verification | `8a1896dba71446ada8b482f66a6f1ed9` |
| Automatic payments and header balances | `d6287f1626b040f0978495a1cc88b2a2` |

Implementation adopts the numbered rail, restrained monochrome panels,
two-column cost explanation, masked phrase grid and funding controls. Generated
sample addresses, fixed fees, throughput, protocol labels and shared-RPC copy
were discarded. The balance refinement also discarded invented protocol
labels, suggested funding amounts, zero-confirmation claims and shared RPC
copy. Interface text is English/Chinese, with native labelled forms,
explicit phrase reveal and responsive layout. Design exports contain masked
placeholders; browser screenshots are taken before any phrase is generated.

Verification includes encrypted backup/recovery and signer policy tests, a
bounded Worker-read regression, actual retained SBF Commit/Reveal execution in
an isolated LiteSVM, and a real browser using the retained complete-model Worker.
Browser RPC/login responses and scientific values in the SBF fixture are explicit
fixtures. They do not establish public Devnet finality, biological accuracy,
mainnet readiness or independent security acceptance.

The existing dependency audit includes advisories in the pre-existing Solana
dependency tree. The new wallet cryptography packages introduce none of the
reported advisories. The native `bigint-buffer` path is not bundled into the
browser; its JavaScript fallback is used in the test environment. No force
upgrade or claim of a clean independent security audit is made.

Mainnet, production payments, additional rewards and main-branch merging remain
disabled. The acceptance report records the precise deployed revision, tests and
remaining real-provider acceptance work.
