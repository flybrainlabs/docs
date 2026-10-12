# flybrainlabs project identity

The current project name and GitHub owner are both `flybrainlabs`. Use this exact
lowercase spelling for project headings, repository descriptions, website
branding, release notes and contributor-facing explanations.

## Maintained repositories

`web`, `node`, `miner`, `explorer`, `protocol`, `contracts`, `sdk`, `infra`,
`research` and `docs` use publication targets under
`https://github.com/flybrainlabs`. The infrastructure release manifest records
whether the source release has actually been verified remotely.
All new documentation, commits, issues, pull requests, release notes and technical
comments are written in English. Product interfaces remain bilingual.

The official website remains `https://flybrain.work/`. The owner's separately
specified social link remains `https://x.com/flybrainwork`. A GitHub account
change does not select a new domain or social account.

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
operations. Verify both identities separately. The retired accounts and their
connectors are not publication targets.

Completed and verified updates are committed and pushed automatically using
normal fast forwards. Preserve remote changes, skip empty commits and refresh
the infrastructure dependency pins. A source release is complete only when every
component and the containing infrastructure commit have been verified remotely.

## Test token naming

The owner separately selected `flybrainwork` as the name of the FBW token on
Solana Devnet. This asset name does not rename the `flybrainlabs` project or
GitHub owner. Its supply and allocation follow the V2 model; immutable legacy
identifiers and production FLY configuration retain their existing meanings.
