# Day 12

Tags: Javascript
Date: November 23, 2022
Status: Done

Task of the day 

- Basic Javascript (24/113)
- Code academy : introduction to Javascript
- Spinamp Building a Web3 Music Experience using the Spindex with Aidan Musnitzky
- Arpeggi Labs 🛠 Use and contribute to the largest on-chain open-source music and sample library: ARP

Notes 

---

This document contains notes on two topics related to Javascript. The first is a Spinamp workshop, which covered tools for building experiences in the web3 music ecosystem, including an embeddable player, a Javascript client SDK, and a set of React hooks for fetching data. The second topic is Arpeggi Labs, which is an open-source, on-chain media library for music creation on Polygon. The ARP protocol tracks attribution and usage, and audio data is stored on Arweave. The notes also include ideas for projects that can be built using ARP, such as an automated DJ mixer and a sample editor.

Spinamp with Aidan Musnitzky

Twitter: @spin_amp

[dev.spinamp.xyz](http://dev.spinamp.xyz)

### Explore, curate, share and listen to the growing public library of web3 artists and minted

![Screen Shot 2022-11-23 at 11.55.26 AM.png](Day%2012%2094650e0671cc4800a2d15eeae0bb0bb9/Screen_Shot_2022-11-23_at_11.55.26_AM.png)

### Spinamp-dev

spinamp-dev is a collection of tools to help you build new experiences for the growing web3 music ecosystem, spinamp-dev is part of the spinamp stack, with our core product being spinamp itself

How do you like to build?

**Spinamp-embed**

An embeddable, customizable, mini spinamp player you can use on your own website.

Embedded.spinamp.xyz

![Screen Shot 2022-11-23 at 12.03.41 PM.png](Day%2012%2094650e0671cc4800a2d15eeae0bb0bb9/Screen_Shot_2022-11-23_at_12.03.41_PM.png)

**Spinamp-sdk**

A javascript client sdk for the growing web3 music ecoysystem, providing to the above spindexer API and upcoming playlist API

**Spinamp-sdk**

A javascript client sdk for the growing web3 music ecosystem, providing to the above spindexer API and upcoming playslit API

**Spinamp-hooks**

A set of react hooks for fetching data from spindex and the upcoming playlist API

Spindexer

- indexing on-chain music nft activity across multiple chains
- Augmenting that on-chain data with additional external info needed (eg: from off-chain, centralized sources, ipfs and arweave, etc)
- Transformning and connecting the data into a more comprehensive, cohesive and standardized schema
- Storing and maintaining an up-date, real-time API a web3 music.

Dependencies

- NodeJS/yarn setup (v18.5.0 recommended)
- Postgres installed (v14.4 recommended)
- Postgres running
- postgresql-client installed
- ts-node installed globally
- git-ifs

Design goals

There are a few design goals for the system:

- Be fast, up to date and have low latency liveness
- Be reliable with minimal/zero maintenance need
- Handle crashes, downtime and errors gracefully, resuming without needing to rebuild the DB or being blocked by external dependencies
- Support both onchain, multichain and centralized data sources
- Allow extensions with additional new contracts and platforms without requiring a DB rebuild nor re-processing from start.
- Allow for decentralization and even some consensus without any co-ordination

---

# Notes

## Arpeggi Labs w/ Kyle Dhillon

ARP: How to use and contribute to the largest on-chain sound library

What is Arpeggi?

- Transparent, open-source, and collaborative music creation platform
- Arpeggi platform (Arpeggi studio homepage) + ARP protocol

arpeggi.io

docs.arpeggi.io

What is the ARP protocol?

- Open-source, on-chain media library, on polygon
- Tracks attribution and usage
- Audio data stored on Arweave (preferably)

docs.arpeggi.io/faq/build-on-arpeggi

---

What can you build with ARP?

- Automated DJ mixer that creates an infinite mix using on-chain stems. Record/register the resulting mixes back on chain for others to use
- In browser step sequencer that uses one-shot
- samples from ARP.Register loops back into ARP for people to use in Arpeggie Studio

In browser sample editor that:

- Build a desktop app allowing dragging samples from the ARP sound library into DAWs like ableton, logic or FL studio
- Build a splits distribution smart contract that automatically rewards sample + stem contributors using Zora Asks 1.1 + Arpeggi’s ARP protocol
- Make a VST plugin (synth or effect) that can be tokenized and integrated into Arpeggi Studio

**KSD_ETH (twitter)**

Q&A and contact info

elementary.audio

Web Audio API