---
title: The beacon chain
description: Everything you need to know about the beacon chain
lang: en
sidebar: true
---

# The conductor: the beacon chain

In a multi-chain world of [shards](/en/eth2/#shard-chains), something needs to ensure that they're all in sync. To understand how this works you'll need to get to grips with a few key concepts.

## Validators

When you try and send ETH to someone, a validator will be responsible for adding your transaction to a block.

A validator is someone who has staked at least 32ETH and now participates in the network by checking transactions, proposing new blocks and validating block proposals. Validators are algorithmically chosen to propose new blocks and if they're not chosen, they're responsibe for validating the proposal.

The amount of transactions a validator can add to a block proposal depends on the size of their stake. A validator with 40ETH behind them can add more transactions than someone with 32ETH.

## Attestors

All other validators will have seen your transaction and although they're not responsible for adding it to the block, they do need to confirm that everything looks as it should.

If a validator agrees with a block proposal they are "attesting" to it. This is like giving the block the "ok" before shipping it off to the beacon chain. 128 validators are required to attest to a block – this is known as a "committee".

## Committees

The committee has a time-frame in which to propose and validate a block. This is known as a "slot". Only one valid block is created per slot. There are 32 slots in an "epoch". After each epoch, the committee is disbanded and reformed with different participants.

New epochs occur every 6.4 minutes.

Eth2 should have at least 64 shard chains to start with, so how are the 63 other chains going to know about your transaction? The beacon chain!

## Crosslinks

Once a new block proposal has enough attestations, a "crosslink" is created which confirms to the beacon chain that it should include that block, and your transaction, in the beacon chain. This is coming in [Phase 1](/en/eth2/roadmap/#phase-one). Once this has happened, the block proposer gets a reward in the form of more ETH.

## Finality

Once a block is ready for the beacon chain, it needs finality. It shouldn't be able to be reverted. The beacon chain uses a protocol known as Casper (Friendly Finality Gadget) to finalise blocks.

### How does Casper work?

Casper uses cryptoeconomic incentives to discourage validators frrom reverting a block. The protocol finalises blocks by requiring 2/3 validators to make a "maximum-odds" bet that the block will be finalised. This bet discourages any bad behaviour because any guilty validators will lose their stakes.

## In summary

The beacon chain receives block attestations from shards and uses Casper FFG to ensure they are finalised.

Prior to that, the shard blocks go through a proof-of-stake process:

- proposed by a chosen validator in a committee
- attested by the rest of the committee during an epoch "slot"
- crosslinked with the beacon chain after enough attestations
- finalised by Casper using cryptoeconomic incentives

## Further reading

For more on the Beacon Chain:

- [The Beacon Chain Ethereum 2.0 explainer you need to read first](https://ethos.dev/beacon-chain/) _– Ethos.dev_
- [Two Point Oh: The Beacon Chain](https://our.status.im/two-point-oh-the-beacon-chain/) _– Status_