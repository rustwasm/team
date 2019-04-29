# Governance of the `rustwasm` Organization

This document describes the lightweight governance structure used in the
[`rustwasm` organization][org].

- [Code of Conduct](#code-of-conduct)
- [Membership](#membership)
- [Teams](#teams)
  - [`@rustwasm/core`](#rustwasmcore)
  - [`@rustwasm/book`](#rustwasmbook)
  - [Creating New Teams](#creating-new-teams)
- [Repositories](#repositories)
  - [Adding New Repositories to `rustwasm`](#adding-new-repositories-to-rustwasm)

## Code of Conduct

We abide by the [Rust Code of Conduct][conduct] and ask that you do as well.

## Membership

Membership into the `rustwasm` GitHub organization is given to anyone who is
involved in Rust and WebAssembly development or otherwise contributing to the
`rustwasm/*` repositories.

Does that describe you or someone you know? Request membership or nominate
someone for membership by contacting anyone in the [`@rustwasm/core`
team][core-team]. We welcome you with open arms!

Note that membership alone does not grant commit access to all of the
repositories in the organization. Commit access is managed by a combination of
the `@rustwasm/*` team membership and on a per-repository basis.

## Teams

Teams make design, architectural, and new-membership decisions for their
relevant domains and repositories by consensus. If consensus can't be made, then
the `@rustwasm/core` team may act as a tie-breaker.

### [`@rustwasm/core`][core-team]

The core team manages the vision and navigates the future for the overall
`rustwasm` organization.

### [`@rustwasm/wasm-pack`][wasmpack-team]

The `wasm-pack` team is made up of frequent contributors to `wasm-pack`. It
is led by [ashleygwilliams] and [drager].

[wasmpack-team]: https://github.com/orgs/rustwasm/teams/wasm-pack
[ashleygwilliams]: https://github.com/ashleygwilliams
[drager]: https://github.com/drager

### Creating New Teams

The [`@rustwasm/core` team][core-team] decides when and whether to create new
teams and which `rustwasm/*` repositories are within the domain of the new team.

## Repositories

Unless otherwise noted, each `rustwasm/*` repository has the following general
policies:

* All pull requests must be reviewed and approved of by at least one relevant
team member or repository collaborator before merging.

* Larger, more nuanced decisions about design, architecture, breaking changes,
trade offs, etc are made by the relevant team and/or repository collaborators
consensus. In other words, decisions on things that aren't straightforward
improvements to or bug fixes for things that already exist in the project.

* If you make two or three significant contributions to a repository, you should
seriously consider requesting collaborator status!

* On the flip side: if you are a collaborator on a `rustwasm/*` repository and
notice that someone has made two or three significant contributions to it, you
should seriously consider nominating them for collaborator status!

### Adding New Repositories to `rustwasm`

The [`@rustwasm/core` team][core-team] decides whether a repository should be
included in the `rustwasm` organization and which if any teams should have
commit access.

[org]: https://github.com/rustwasm
[conduct]: https://www.rust-lang.org/en-US/conduct.html
[core-team]: https://github.com/orgs/rustwasm/teams/core/members
[book-team]: https://github.com/orgs/rustwasm/teams/book/members
