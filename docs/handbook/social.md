# Community contributions and Social

[Open Social ↗](/social/) to connect your community identity, complete a verified
contribution and see where your points place you on the real leaderboard.
The page is open to visitors; only participation requires a signed-in wallet.

## What the community budget means

The page highlights **25,000,000 FBW** for future community airdrops. This budget
comes from the existing **31,183,323 FBW Community & Ecosystem Pool**. The remaining
**6,183,323 FBW** is retained for other community and ecosystem uses.

| Use within the community pool | FBW | Share of this pool |
|---|---:|---:|
| Future community airdrops | 25,000,000 | Approximately 80.17% |
| Other ecosystem uses | 6,183,323 | Approximately 19.83% |
| Community & Ecosystem Pool | 31,183,323 | 100% |

“Over 80%” refers to this pool, not total token supply. This is a budget allocation:
it does not create new tokens or mean tokens have already been sent or locked in
a dedicated on-chain vault. The existing FBW asset is on Solana Devnet.

**Points are not FBW.** Verified points determine your community rank and will be
considered in future allocations. There is no fixed point-to-token conversion,
guaranteed personal amount or announced distribution date. Before a real
distribution, its eligibility, cutoff, calculation and claim terms must be
published and authorized. Completing a task now updates points, not your wallet's
token balance.

## The five sections

| Section | What you can learn or do |
|---|---|
| Community Airdrop Allocation | Understand the budget and its place in the pool |
| My Community | Read your actual points, rank, completed tasks and X identity |
| Community Tasks | Start available tasks and follow their verification state |
| Community Leaderboard | Browse verified community contribution rankings |
| Activity | Read the dated point entries behind your personal total |

There are no sample participants inserted into the live leaderboard. An empty
ranking means there are no eligible positive community contributions yet. Your
personal rank remains available even if you are outside the first 100.

:::diagram social

## Connect a wallet and sign in

Use the same wallet button as elsewhere on the website. Connect a Wallet Standard
Solana provider, select your account, then sign the sign-in message. Connecting an
account and proving control of it are separate steps. Sign-in is a message
signature: it does not authorize a transfer or require a network transaction fee.

A refresh can restore your previously selected provider and account silently
when the wallet supports it. A matching unexpired login remains in the same tab.
A locked/missing provider or expired login may require your action. Explicitly
disconnecting keeps the account disconnected; changing accounts clears the old
participant's private view. Learn more in [wallet connection and sign-in](/docs/wallets/).

Social participation does not require an active mining grant or an unfinished
scientific target. Community points and scientific mining rewards are distinct.
The website never treats your token balance as your community score.

## Verify your X identity

The first available task is **Connect X Identity**. Its initial reward is
**100 Community Points**. It is a one-time contribution for each wallet and known
X identity. The server defines the reward; your browser cannot choose it.

### 1. Generate your verification post

Choose **Start verification** after signing in. The site creates a random public
challenge valid for **30 minutes**, bound to your wallet and current login.
The code starts with `FBW-VERIFY-` and is shown with its expiration.

Choose a neutral identity statement or a project introduction. You may edit the
text. Keep the entire code in the **original post body**. The reward does not
change with wording, promotional tone or engagement. A positive endorsement is
not required. Follows, likes and reposts are not rewarded by this task.

Generating another challenge invalidates the previous one. Use the current code,
not a screenshot or saved older post text. Refreshing the same signed-in tab can
recover an active challenge and its submitted URL.

### 2. Publish on X

Copy the text or select **Post on X**. X opens its own posting screen and you
confirm publication yourself. The website does not post for you and does not
request an X password, cookie or access token.

Keep the post public while it is being checked. A private or unavailable post may
not provide usable evidence. Put the code directly in your own body text;
embedding it only in a picture, link, display name or quoted post is insufficient.

### 3. Submit your post URL

Return to Social, paste an HTTPS X/Twitter status URL and select **Verify post**.
The backend reads official public oEmbed evidence, checks the actual author and
status identity, then finds the code in the original body. It also checks expiry,
session control, prior wallet completion, known identity conflicts and post reuse.

When all checks pass, binding, completion, points and history are saved together.
The page shows **X Identity Connected**, your admitted point reward, updated total
and real rank. The verified post and time remain available in My Community.
Refresh reads the stored result; it does not award the task again.

## Understand verification states

| State | Meaning | Useful action |
|---|---|---|
| Available | You have not completed the task | Start a challenge after sign-in |
| In progress | A challenge is active | Publish its code and submit the URL |
| Pending verification | A backend check is running | Wait; refresh can recover the state |
| Needs review | Available evidence or identity checks are insufficient | Keep the original evidence available for review |
| Completed | The contribution is recorded | Read your points, rank and post record |
| Expired | The code is outside its 30-minute window | Generate and publish a new challenge |

An unavailable X provider, unverifiable author or incomplete original body does
not produce points. The request is saved for review. A reviewer must inspect the
original public post and actual author; copying the challenge into a form is not
proof. Expired challenges or original login sessions require a new challenge.
If review rejects the evidence, the page explains the result and permits a fresh
attempt under the published task rules.

The public oEmbed method establishes **challenge_verified** control. It is not
OAuth and may not provide a stable numeric X user ID. That field remains empty.
X usernames can change or be reassigned; disputed changes need review. Official
OAuth verification is a future identity upgrade, not a claimed current feature.

## Points and the leaderboard

Each point change has a source and timestamp. Successful task completion appends
one contribution entry. Corrections append a separate audited adjustment; the
old entry remains. A retry, extra click or refresh cannot create a second first
reward. The reward captured when your challenge was created remains fixed even
if the administrator later changes points for new challenges.

The leaderboard considers effective positive community points. Higher totals
rank first. Ties use the time the current score was reached, then a stable wallet
address. A reviewed account may temporarily be excluded from public ranking
without erasing its ledger. Review and corrections leave administrative records.
Mining throughput, stake and token holdings do not affect this leaderboard.

Use **Refresh** to request current results, or load more ranking/activity rows.
A live leaderboard can change while you paginate. An approved immutable snapshot
is the record used for a reproducible allocation, rather than an arbitrary later
screen capture.

## Privacy and identity settings

The public leaderboard displays a shortened wallet address. You can copy it or
open its public contribution details. Showing your verified X username is
**optional** and starts off by default. Enable the setting in My Community to
publish it beside your rank.

A public verification post itself remains public on X. The public contribution
feed omits your session, private review reasons and administrator evidence.
These are different privacy boundaries: choosing not to show the username on the
leaderboard does not make an X post private.

You can unlink your X identity after a fresh wallet sign-in. Earned points and
first-task completion remain. Unlinking does not permit another first reward or
allow another wallet to reuse the known identity's first contribution.

## Future allocations and administration

Authorized administrators can review original evidence, configure tasks, append
point corrections, mark account disputes and freeze rankings. A snapshot records
cutoff, rules, points, rank, eligibility and content hash; it cannot be overwritten.
Corrections preserve the previous snapshot and create an audited successor.

Candidate allocations use a selected frozen snapshot, an explicit finite budget
and versioned rules. The current preparation engine distributes exact integer
atoms proportionally to eligible points and resolves remainders by stable rank.
A candidate does not reserve funds. Approval reserves an internal amount only
after snapshot approval and rule publication, and all approved reservations count
against the 25,000,000 FBW limit. Cancellation records a release rather than
removing history.

CSV/JSON exports are preparation artifacts. They do not send tokens, provide an
immediate claim or establish a universal conversion rate. Actual future transfers
require a separately authorized execution process and verified chain evidence.

## Common questions

**Why is my token balance unchanged after verification?** You earned community
points. Points and FBW balances are different records.

**Why does the page say Needs review?** The backend could not establish sufficient
public evidence or resolve an identity conflict. No success is assumed.

**Can I earn the first reward again after unlinking?** No. Historical completion
and known identity uniqueness remain intact.

**Why does a refresh ask me to sign in?** The selected wallet can remain connected
while its login expires. A new signature proves control; it is not a transfer.

**What happens if there is no rank yet?** An account without eligible positive
community points is not ranked. This is an actual empty state.

**Is an airdrop scheduled?** No date or guaranteed amount is announced by this
module. Applicable allocation terms must be published before any actual execution.

For operators and integrators, read the maintained technical delivery document
`docs/social-community-system.md` in the docs component. For asset identity and
receipt scope, read [FBW Devnet reference](/docs/devnet/) and
[economic model](/docs/economics/).
