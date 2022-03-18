# Open Questions & Next Steps

## Questions

### 3/17

- Should we be using the ERC721 standard here? Is it worth it to override `transfer()`?
- Can we "easily" handle a rollup data format?
- Does an array of signatures work for handling attestations in this version? 

### 3/14
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

## Next Steps

### 3/17

- stump functions
- dbdiagram
- `mint()` & initial deploy tests

### 3/11

- Talk to flip
- Drop a schema for the database
- Setup contract template
- Maybe start contract dev next week

### 3/8

- Finalize Contract requirements
- Investigate some protocols
- Continue refine the rest of the doc
- Setup up repo

