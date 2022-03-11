# Govrn Protocol Tech Spec

### Contributors
- Keating
- Scott

### Overview
![](https://i.imgur.com/bD7l4fJ.png)



### Technologies Required

- Contract for Non-transferrable NFTs
- 

### Components


#### Solidity

Contribution Model

|name| type | storage | note |
|----|------|------|------|
| Identifier | string |     |     |
| Date of Submission | datetime |     |     |
| Date of Engagement | datetime |     |     |
| Name | string |     |     |
| Details | text |     |     |
| Proof | string: link | link to an image/ceramic metadata |     |
| Partners in Contribution | string | list |     |
| Time Scope | options | currently, something else, not sure |
| Attestations | array of attestors |     |

#### Procotols and Design

__Requirements__

- Non-transferrable
- Conforms to ERC721 for visibility in ecosystem
- Can mint to any address
- Specific templates for each activity
- Allow template and activity to be created simultaneously

__Flows__

![](https://i.imgur.com/iI6WILE.png)

__Functions__

```solidity
function mintContribution(
    string identifier,
    uint256 date_of_engagement,
    string name, // template? has details
    string notes,
    string proof,
    string[] partners_in_contribution,
)
function attestContribution(
    string identifier,
)
function bulkMint()
function bulkAttest()
```

__Events__

```solidity
event ContributionMinted()
event ContributionAttested()
```

#### Backend

- Subgraph
- Bot
    - Discord Receiver
- Data Pipelines (Plugins)
    - Twitter API
    - Github
    - Discourse
    - SourceCred
    - StackExchange

Pre-Processing

- Contribution Staging
- Schema

#### Frontend

- Reporting Interface(s)
    - Web Form
        - Use list of contributions
        - Create freeform and use
    - Discord - Kevin
- Attestation Interface
    - bulk select
    - search for specific users or addresses
    - filter by dao
- A feed contributions
    - Contributions added and received
- Email notification with summary
- Dashboard with reporting

### Questions
1. Are there any existing procotols we could leverage to generate these NFTs?
    - ERC721 compatible
        - Nontransferable, [Maker Badges](https://github.com/naszam/maker-badges)
        - Potentially leverage maker badges for non-transferability, and have a make template and create
        - Include receiver in mint so you can mint for others
    - Permissionless Minting of Contributions
        - gasless
    - Template editor(s)
2. Which plarforms do we prioritize for automated reporting?
    - twitter
    - github
    - sourceCred?
3. How we handle users/Daos attesting to a transaction? How do we prevent sybil attacks? Is their protocols we can leverage here.
    - Can we update the metadata of the NFT?
        - Have another NFT that relates back?
        - We can potentially update the NFT uri?
            - Permissioning would be tricky
    - Sybil Solutions
6. Do we need to handle displaying any data?
    - Subgraph to track these on chain
8. What do we store on chain vs in a Ceramic document?
9. What can we leverage for Sybil resistance?
      - BrightID/Proof Of Hummanity
          - Clr.fund Bright Id integration could be useful
      - Sybil Detection DAO (Gitcoin/Metapod)
10. Do we mint on report or we wait until it is validated? Maybe gasless, or have them mint, attest to their own contributions. 
      - Do we allow others to mint for me and then can I attest to that?
      - If I tweet about govrn, do I need to attest to that, then Kevin minted that tweet and then I can confirm.


### Next Steps

3/11
- Talk to flip
- Drop a schema for the database
- Setup contract template
- Maybe start contract dev next week

3/8
- Finalize Contract requirements
- Investigate some protocols
- Continue refine the rest of the doc
- Setup up repo
