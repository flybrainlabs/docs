# flybrainlabs project identity

The maintained project name and GitHub owner are both `flybrainlabs`. Use this
exact lowercase spelling for source ownership, repository descriptions and
contributor-facing technical explanations.

**flybrainwork** is the public website name. Website wordmarks, page titles,
metadata and reader-facing product introductions use this name. The official
website is `https://flybrain.work/`.

## Maintained repositories

`web`, `node`, `miner`, `explorer`, `protocol`, `contracts`, `sdk`, `infra`,
`research` and `docs` use publication targets under
`https://github.com/flybrainlabs`. The infrastructure release manifest records
whether the source release has actually been verified remotely.
Technical maintenance documentation, source code, code comments, commits, issues,
pull requests and release notes use English. Chinese prose is allowed in the
localized Markdown handbook under `docs/handbook/zh/`, with translated labels in
its `navigation.json`. Code examples and technical comments remain English,
including inside translated documents. Product interfaces remain bilingual.

The official social link is `https://x.com/flybrainwork`.

## Compatibility identifiers

Existing scientific hash domains, fixed receipt bytes, protocol schema names,
storage keys, historical service names and internal Rust crate identifiers are
retained where required by the registered protocol and existing deployments.
They identify compatible machine interfaces; they are not the current project
brand. Changing those inputs requires an explicit versioned migration and
verification of existing records, balances and stored models.

Project branding must never cause a wallet, identity, result, dataset, model cache
or browser profile to be recreated. The infrastructure ownership maps and release
pins keep the maintained sources distinct from persistent runtime state.

## Publication identity

Use the dedicated `github-flybrainlabs` SSH alias for Git publication and an
isolated GitHub CLI configuration that authenticates as `flybrainlabs` for account
operations. Verify both identities separately. Publication targets are limited
to the maintained repositories under `flybrainlabs`.

Completed and verified updates are committed and pushed automatically using
normal fast forwards. Preserve remote changes, skip empty commits and refresh
the infrastructure dependency pins. A source release is complete only when every
component and the containing infrastructure commit have been verified remotely.

## Test token naming

The FBW token on Solana Devnet is named `flybrainwork`. Its supply and allocation
follow the V2 model; immutable legacy identifiers and production FBW
configuration retain their existing meanings.

## Current public token and compact navigation

The token name is flybrainwork and its public symbol is FBW. Current website
labels, guides and whitepaper explanations use FBW. Frozen scientific/financial
objects and archived contracts retain their exact original bytes. The existing
mint and its supply/authorities are unchanged by a label update.

Compact website headers place language selection inside the navigation menu.
The language row comes first, outside the independently scrolling links, so it
is visible immediately on short screens. Navigation links use two columns in the
compact layout and remain accessible when the Resources disclosure is expanded.
Documentation panels use normal flow, responsive disclosures and bounded scroll
regions so that controls do not overlap the prose. See the public handbook and
its maintenance guide for the current reading and build behavior.
