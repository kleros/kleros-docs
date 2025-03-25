
# Guide for Drawing Jurors Manually

`KlerosLiquid` draws jurors randomly. Anyone could do this task, even the users. The Kleros Cooperative runs the [following bot](https://github.com/kleros/action-callback-bots/) to take care of it automatically.

Sometimes the bots break because of...
* RPC service degradation, 
* Transactions getting stuck, 
* Not enough gas in bot wallets, 
* Programming errors. 

The users are not expected to worry about this upkeep, but anyone willing to pay for gas may draw the jurors manually. Although there is no frontend functionality to draw the jurors, it can be done by calling the contracts directly.

## Procedure

It is useful to know [KlerosLiquid uses three phases](https://github.com/kleros/kleros/blob/master/contracts/kleros/KlerosLiquid.sol#L390) to obtain randomness in a safe way:
* Phase 0: `staking`
* Phase 1: `generating`
* Phase 2: `drawing`

Steps: 
1. In order to draw the jurors, you need to be in Drawing phase (`phase == 2`). to do so, just call `passPhase` when able. you can use block explorer tools such as etherscan or blockscout. (on gnosis chain, these functions are called through "Write Proxy").
2. Look for disputes that are still missing jurors to draw, for example on the [KlerosBoard](https://klerosboard.com/#/100/cases).
3. Call `drawJurors` , you will pass the id of the dispute, and in `_iterations` the number of needed jurors.

## Resources

* Ethereum Mainnet KlerosLiquid [https://etherscan.io/address/0x988b3a538b618c7a603e1c11ab82cd16dbe28069](https://etherscan.io/address/0x988b3a538b618c7a603e1c11ab82cd16dbe28069)
* Gnosis Chain KlerosLiquid [https://blockscout.com/xdai/mainnet/address/0x9C1dA9A04925bDfDedf0f6421bC7EEa8305F9002](https://blockscout.com/xdai/mainnet/address/0x9C1dA9A04925bDfDedf0f6421bC7EEa8305F9002)