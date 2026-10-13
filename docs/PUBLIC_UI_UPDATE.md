# flybrainwork public UI update

Release: `public-ui-20261013-v1`, published on 2026-10-13.

## Names and retained identities

The website UI name is **flybrainwork**. Header/footer wordmarks, page titles,
Open Graph site/title metadata, translated introductions, public community post
wording and the handbook use this name. The maintained project, GitHub owner and
ten repository publication targets remain **flybrainlabs**. The existing token
name is flybrainwork and its public symbol is **FBW**.

Existing logo files keep their paths; the download uses the public display name.
Scientific and financial schema names, signature domains, frozen policy bytes,
token identity, wallet permissions and persistent storage keys retain their
existing meanings. No asset was reissued or paid again for this UI release.

## Compact navigation

At widths up to 1,200 CSS pixels, the existing language button moves to the first
row of the menu. It remains outside the scrolling navigation links. The links
use two columns, with Resources spanning both. The menu's height is bounded by
the small viewport height; longer resource lists scroll inside their own region.
The header and document remain in normal flow.

Opening the menu resets only its link scroll position. Language selection does
not scroll the document. Returning to a wider viewport restores the same button
and its listeners to the desktop header; there is one language control.

## Task availability and a missing historical claim

The signed current-round and readiness responses identified the pinned authority
and returned `RESEARCH_STAGE_COMPLETE`, no open round, zero pending/unopened goals
and exhausted supply. The four related services were active. Task availability
and claim lookup are separate operations. Restarting a service does not append a
calibrated plan or restore an exhausted finite paid budget.

The reported claim endpoint returned HTTP 404 with `NOT_FOUND: claim`. A local
candidate can have a calculated claim ID before the authority admits it. If the
signed historical round is closed, its deadline has passed and the local record
has no acceptance receipt, reconciliation records **Round closed · candidate not
admitted; results retained** and retires automatic polling. It retains candidate
identities, metrics and artifacts; it does not create a winner or payment.

Receipted claims, open rounds and other HTTP/transport errors keep their existing
reconciliation behavior. A 404 is not accepted as proof of a financial outcome.
New rewarded work requires a prospectively calibrated task and a newly frozen
finite budget. The prior two-unit Devnet acceptance plan remains completed.

## Verification and scope

The compact/document regression checks 24 reading layouts and eight short-screen
language/layout cases in each local and public run. Short cases include 320×480,
390×568, 667×320 and 1024×600, in English and Chinese. Checks use viewport bounds
and pointer hit testing before clicking, then expand and scroll Resources to
verify language visibility and access to the final link. They also check prose
reflow, desktop language placement and unchanged public FBW allocation values.

All 56 rendered page shells use the selected UI name. The complete static release
and handbook links, anchors, search index and Markdown hashes passed validation.
Four branding tests, eight static-export tests, nine candidate reconciliation
cases and native library compilation passed. Public HTTP comparison matched 70
changed uncompressed objects plus nine retained core/configuration objects.
Deployment verified a backup and the remote hashes of 80 scoped objects.

These browser tests use Chromium emulation. They do not establish physical
Android/GPU acceptance or actual extension-wallet confirmation. No model cache,
browser profile, database or financial budget was reset.

Acceptance: [Public UI record](https://github.com/flybrainlabs/infra/blob/main/docs/PUBLIC_UI_ACCEPTANCE.json).
