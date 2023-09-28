# Day 8

Tags: Solidity, css
Date: November 19, 2022
Status: Done

Task of the day

- Technical documentation page (review later)
- CSS Variables
- CSS Grid
- ****[Metabolism Technical Summit - ZORA’s Create Tools](https://www.youtube.com/watch?v=hwoWfoweh7k)****

---

Notes

Start-time: 10am

End-time: N/A

****Metabolism Technical Summit - ZORA’s Create Tools****

- Iain Nash
- Creator contract and build on front-end
- Zora docs

![Screen Shot 2022-11-19 at 10.46.03 AM.png](Day%208%202b3538fee2354e2d89f9bd0286d7d3cd/Screen_Shot_2022-11-19_at_10.46.03_AM.png)

Main create contracts involve:

- **ZoraNftCreator**: a factory that deploys new NFT contracts
- **ERC721Drop**: A template NFT contract that is used to create a new collection
- **Edition meta renderer**: Renders metadata for an Edition NFT
- **DropMetaRenderer**: Renders metadata for a drop NFT

**Look into how to create a smart contract: **Create edition function**

Breakdown of the elements within a smart contract:

1. Contract ZoraNFTCreator{
2. function createEdition{
3. name string —> name of the NFT ** you can’t edit this once deployed
4. Symbol string —> symbol for you NFT ** you can’t edit this once deployed
5. Editions size uint —> max amount that can be minted | There’s also the option to create an open edition. 
6. RoyaltyBPS uint, —> The royalty factor of when you sell an NFT
7. DefaultAdmin address —→ The address that manages the contract
8. FundRecipient address —> it’s the person that receives the funds 
9. salesConfig SalesConfig ** the argument against lazy minting ?
10. Description string —> the description text of the NFT
11. AnimationURI string —> It defines the media (Audio, webpage, etc)shown for the NFT
12. imageURI string —> It defines the image shown for the NFT
13. ) external

Javascript 

![Screen Shot 2022-11-19 at 11.09.15 AM.png](Day%208%202b3538fee2354e2d89f9bd0286d7d3cd/Screen_Shot_2022-11-19_at_11.09.15_AM.png)

** the “ipfs” is a decentralized server and ensures that you don’t lose your content if a server crashes.

Sales config

![Screen Shot 2022-11-19 at 11.12.13 AM.png](Day%208%202b3538fee2354e2d89f9bd0286d7d3cd/Screen_Shot_2022-11-19_at_11.12.13_AM.png)

** WolframAlpha for unix time, useful for public sale starts and end time 

** The merkle route is a predefined way of determining all of these different users if they exist withing the set. ( it helps with setting up a pre-sale function). If you don’t want to use it, just set it to 0.

[](https://zora-essay-edition-minter.vercel.app/create)

WAGMI : Hook library for interacting with Ethereum