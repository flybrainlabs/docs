# Your first session

A useful first session begins with understanding the current task supply. The model can be prepared while a funded stage is complete, but preparation does not create a new payable task. Check the mining page and [Feature availability](/docs/availability/) before expecting a reward.

## Choose a starting path

| Your goal | Start here | Next action |
| --- | --- | --- |
| Understand the project | [Project overview](/docs/overview/) | Follow the system diagram and model guide |
| Explore anatomy | [Neuron atlas](/atlas/) | Search a type, select its representative and read provenance |
| Inspect an existing outcome | [Explorer](/explorer/) or [Results](/results/) | Follow a candidate or reproduction package |
| Prepare for computation | [Mining](/mining/) | Read the preparation status and storage requirements |
| Request scoped work | [Compute services](/services/) | Describe the scope and obtain a private ticket |

## Prepare the browser

Use a browser supporting WebAssembly and workers. The workflow also uses persistent browser storage to reuse model chunks and retain results. Ordinary browsing and a private/incognito session may have different persistence behavior. Keep the same browser profile when returning to saved work.

Open [Mining](/mining/) and review the displayed task, preparation and wallet states. Starting preparation is an explicit action. Allow the verified data download and model construction to finish; reopening other pages does not need another complete download when the retained cache is valid.

:::diagram preparation

The progress display follows the active phase. During download, watch transferred bytes and integrity checks. During build, watch model construction. During mining, watch candidate progress and actual throughput. A completed download alone does not mean the executable model is ready.

## Wallet setup for funded work

When a funded plan is available, connect a compatible Wallet Standard wallet, confirm the selected account, complete sign-in and review the finite grant transaction. These are separate steps with separate permissions. Read [Wallet connection and sign-in](/docs/wallets/) and [Grants, rent and refunds](/docs/grants/) before approving a transaction.

The initial Devnet plan is completed and rejects new deposits. Connecting a wallet or preparing the model cannot reopen that plan. Wait for a new frozen plan rather than submitting another deposit for the old one.

## During a computation

Keep the page available, use the worker and graphics controls according to your device, and watch the actual work counters. Pause when you need to reduce activity. Save or export a recoverable result when appropriate. Do not assume an interrupted partial background qualifies as a complete candidate.

A candidate progresses through local qualification, submission, verification and winner selection. A wallet reward is received only after finalized settlement evidence. The [Mining workflow](/docs/mining/) explains these states in order.

## Preserve a useful record

Record the task or round ID, candidate ID and any public transaction signature. Keep exported packages in a location you control. Public result packages contain their declared scope and checksums; private browser records should remain private unless you deliberately share them.

If something fails, use [Troubleshooting](/docs/troubleshooting/) before clearing storage. A report with browser version, stage, public identifiers and the visible error is more useful than a screenshot of a spinner alone. Never include recovery phrases, private keys or session credentials.
