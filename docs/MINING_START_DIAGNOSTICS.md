# Mining admission and prepared-worker diagnostics

## Observed failure boundary

The owner reported a prepared worker, zero computing workers, an open goal and
the generic retained-work error. Live read-only checks on 2026-10-13 confirmed
that the authority, Wallet Mining V3 gateway and serial verifier services were
active. The authority still supplied round 32, with one additional queued goal.
The reported historical claim lookup returned `NOT_FOUND: claim`; it was not a
task-supply lookup.

An isolated Chromium reproduction showed a specific client defect: a connected,
signed-in fixture wallet without a rent grant still received the **Start mining**
action. Its admission check threw an unclassified rent-grant error, rendered as
the same generic message reported by the owner. This establishes a reproducible
failure path. It does not establish the original user's exact wallet condition;
the original technical diagnostic is still needed for that conclusion.

## Corrections

- Model preparation, open task state, login, balance synchronization and rent
  authorization have separate presentation states.
- The main control opens an explicit finite-grant review when credit is missing.
  It offers device renewal when the selected grant's key is unavailable here.
- The admission check preserves fresh gateway identity, approved-budget adoption,
  finalized balance/rent reads and nonextractable device-key checks.
- Missing grants, insufficient limits and missing device keys use structured
  error codes and readable English/Chinese recovery instructions.
- Scheduler admission faults surface their original diagnostics. Network/storage
  faults are no longer all presented as funding failures.
- A selected candidate with a transport failure before worker dispatch remains at
  the front of the resume queue. Explicit retry preserves its input and original
  funding scope instead of silently skipping an uncomputed candidate.
- Funding-error scope includes the wallet, stage, goal, grant generation and
  credit limits; a prior scope cannot block a renewed grant or another account.
- Opening or canceling a review starts no worker and creates no transaction.
  Completing authorization does not automatically start computation.

## Retention and acceptance boundaries

No token issuance, budget renewal, reward payout or production-fund action is
part of this correction. Public tasks are left for participants. Scientific
identity bytes, economic policy, model caches, candidate artifacts, browser
connection preferences, databases and chain grant limits are retained.

Chromium admission tests use an isolated scripted provider, fixture login/balance
and rent responses and the actual public open round. Prepared-worker presentation
is a fixture. These tests do not establish real extension confirmation, full-model
execution on the owner's device, physical Android/GPU acceptance or independent
operator/scientific validation.
