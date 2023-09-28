# Day 5

Tags: HTML, Solidity, css
Date: November 16, 2022
Status: Done

Tasks of the day

- Survey form (Free bootcamp)
- CSS box model
- CSS Flexbox —> Look into [https://flexboxfroggy.com](https://flexboxfroggy.com/)
- [Beyond the edition: custom IERC721Drop extensions for fun & profit](https://www.youtube.com/watch?v=s0Ye2Z02MwA)

---

### Notes

Beyond the edition: custom ERC721Drop extensions for fun & profit

- Zora creates: it manages a smart contract
- Making custom minting modules

** This is an advanced course and an intro to solidity course is suggested before using 

Function: createEdition

![Screen Shot 2022-11-16 at 7.48.46 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_7.48.46_AM.png)

Details of the editions include:

- Description
- AnimationURI
- ImageURI

Function: Create drop

![Screen Shot 2022-11-16 at 7.52.11 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_7.52.11_AM.png)

Details of the “create drop” include:

- MetadataURIBase
- MetadataContractURI

** Check out Foundry Ethererum —> [https://www.paradigm.xyz/2021/12/introducing-the-foundry-ethereum-development-toolbox](https://www.paradigm.xyz/2021/12/introducing-the-foundry-ethereum-development-toolbox)

Function: setupDropsContract

![Screen Shot 2022-11-16 at 7.55.41 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_7.55.41_AM.png)

Details of the “setup drop” include:

- IMetadataRenderer metadataRenderer

Interface: IMetadataRenderer

![Screen Shot 2022-11-16 at 7.57.06 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_7.57.06_AM.png)

Contract :Edition MetadataRenderer 

![Screen Shot 2022-11-16 at 8.01.06 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_8.01.06_AM.png)

**This is all available on GitHub (OurZora)**

Storing Data

![Screen Shot 2022-11-16 at 8.21.38 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_8.21.38_AM.png)

Make a metadata renderer for multiple drops. 

- Store mapping

Constructors

![Screen Shot 2022-11-16 at 8.26.45 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_8.26.45_AM.png)

Initialize with data

![Screen Shot 2022-11-16 at 8.31.40 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_8.31.40_AM.png)

Metadata render admin check 

![Screen Shot 2022-11-16 at 8.32.55 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_8.32.55_AM.png)

Custom minters

![Screen Shot 2022-11-16 at 8.33.40 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_8.33.40_AM.png)

Minter example

![Screen Shot 2022-11-16 at 8.39.08 AM.png](Day%205%204de0de799df74bdebfaac26c862f2180/Screen_Shot_2022-11-16_at_8.39.08_AM.png)