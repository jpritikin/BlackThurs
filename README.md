# Black Thursday Compensation Contract

## Background

From March 12-19, ETH (and BAT) suffered a quick drop. This created enormous network traffic. During some spans of time, the Maker price oracle failed to update due to unexpectedly high gas prices. Keepers bidding on auctions also had trouble with gas prices and with a lack of DAI liquidity. Many auctions settled with ETH valued at 0 DAI, or at far less than the market price. 

Most of these losses were absorbed by the Maker protocol and have been recapitalized via Flop auctions. However, vault owners also suffered some losses.

**This was not unexpected.** Normal price fluctuations can easily wipe 100% of the collateral in vaults, even when auctions and oracles are operating optimally. [Additional details here.](https://blog.makerdao.com/the-market-collapse-of-march-12-2020-how-it-impacted-makerdao/)

However, the unusual circumstances left some vaults with less residual collateral then they might otherwise have had. Some vaults may legitimately expect to be left with a non-zero amount of ETH/BAT after a smoothly running auction had paid off their debt. The DAI value of vault holder losses (beyond what might be expected) had the protocol operated optimally has been roughly estimated to be less than 4 million.

[An initial poll on whether to compensate vault holders has passed.](https://vote.makerdao.com/polling-proposal/qmwfvvguaf8rz8xwgv2cqnzzt9t5h6epzh17qmk2ue99y4)

## Compensation Contract Requirements

- The compensation contract will be created on Ethereum.
- The contract will store accounts and compensation amounts. Compensation amounts will be stored as amounts of DAI.
- During creation, data will be added to the contract using multiple transactions. There is too much data to load in a single transaction. Once data is loaded, the API to load data will be locked to the contract creator.
- It shall be possible to continue to add more data using a multisig authorization. The keys in the multisig represent the compensation committee that shall review claims submitted by vault owners who were omitted from the initial compensation class.
- A MKR executive will fund the contract with the required amount of DAI.
- To claim compensation, vault owners will call a no-argument function claim() from a static webpage. The contract will send back the compensation amount to the caller based on the caller's Ethereum address. The caller's address and amount shall be erased from the compensation contract.
- The compensation contract will have a function to transfer any remaining balance back to the surplus account and self-destruct. This function will be callable only by MKR executive.

## Static webpage

The static webpage will state:

> You acknowledge that risks of vault total loss were well documented in multiple places. Maker governance does not accept liability for any past losses experienced by any vault holder, nor accepts liability for future losses.
> The present loss compensation is an exceptional circumstance, and should be regarded as a beneficent gesture. Maker governance has **no obligation** to issue any compensation for losses.
> By accepting compensation, the claimant waives the possibility of future litigation for any vault auction losses that accrued during March 2020.

- This isn't an airtight legal gesture, but it is better than nothing.
- Vault holders who claim compensation should not be tempted to join as a plaintiff in a legal suit against some organization that supports the Maker protocol.
