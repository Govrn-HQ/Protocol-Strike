# Govrn Protocol v1 Overview

## Goals

| goal | description  |
|------|--------------|
| deploy core protocol functionality | create a flexible protocol that creates on-chain data objects based on a user based oracle of off chain, IRL, and on chain contribution events (e.g. tweeting about the DOA, onboarding a new member, running DAO initiative) | 
| automate the contribution reporting from common platforms | integrate a process to automate the pulling and reporting of contributions from most common platforms (e.g. twitter, discourse, etc.)
| store/reference on chain | create on chain records or attestations that either store the contribution data or provide a reference to the contribution data | 

## Technologies Required

- Contract for Contributions & Attestations
- Subgraph to track on-chain data
- Backend to stage data and handle automated processing
- Bot for interfacing with contributors
- Web interface for contribution management and attestations

## Components

### Solidity

`Contribution` Model

|name| type | storage | note |
|----|------|------|------|
| Identifier | string |     |     |
| Date of Submission | datetime |     |     |
| Date of Engagement | datetime |     |     |
| Name | string |     |     |
| Details | text |     |     |
| Proof | string: link | link to an image/ceramic metadata |     |
| Partners in Contribution | string | list |     |
| Attestations | array of attestor's signatures |     |

### Procotols and Design

#### Requirements

- Transferrable??
- Conforms to ERC721 for visibility in ecosystem
  - `balances` and `owners` mappings
  - `name` and `symbol` views
  - `ownerOf()`
  - `balanceOf()`
  - `tokenURI()`
- Can mint to any address
- Specific templates for each activity
- Allow template and activity to be created simultaneously, i.e. "freeform" i.e. `mintTemplateAndContribution()`

#### Flows

![](https://i.imgur.com/iI6WILE.png)

#### Functions

```solidity
function contributionTemplate()
function mintContribution(
    string identifier,
    uint256 date_of_engagement,
    string name, // template? has details
    string notes,
    string proof,
    string[] partners_in_contribution,
)
function mintTemplateAndContribution()
function attestContribution(
    string identifier,
)
function bulkMint()
function bulkAttest()
```

#### Events

```solidity
event ContributionTemplateMinted()
event ContributionMinted()
event ContributionAttested()
```

#### Minion Interaction

Moloch DAOs can interact with the govrn protocol via minions. Calling `attest` will submit the attestation on behalf of the DAO.

### Backend

- [Subgraph](./Subgraph.md)
- [Bot](./Bot_Spec.md)
    - Discord Receiver
- [Data Pipelines (Plugins)](./Data_Pipelines.md)
    - Twitter API [1]
    - Github [2]
    - Discord [3]
    - Discourse [+]
    - SourceCred [+]
    - StackExchange [+]
- [DB Schema](https://dbdiagram.io/d/623520f00ac038740c5e0a0a)
- [Email notification](./Notifications.md) with summary

Pre-Processing

- Contribution Staging
- Schema

### Frontend

- [Reporting Interface(s)](./Reporting_Form.md)
    - Web Form
        - Use list of contributions
        - Create freeform and use
    - [Discord - Kevin](./Bot_Spec.md)
- [Attestation Interface](./Attestation.md)
    - bulk select
    - search for specific users or addresses
    - filter by dao
- [Contribution Portal](./Contribution_Portal.md)
    - Contributions added and received
- [Dashboard with reporting](./Organization_Reporting.md)

## Supported Networks

The initial take is to complete the integration for a single chain assuming DAOs and contributors are on that chain. We'll set aside some research opportunities to understand how [Multi Chain attestations](](./Multi_Chain_Protocol)) could be counted by partners.

### Primary Chain
- Gnosis Chain

### Secondary Chains
- Polygon
- Arbitrum
- Optimism

Chain differences are minimal so deploying the main contract to multiple chains is straight forward it to get rolling assuming the universes don't want to co-mingle. 

## Contributors
- Keating
- Scott

---

## [Open Questions & Next Steps](./Open_Questions.md)

## [Glossary](./Glossary.md)
