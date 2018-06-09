## Charity Sea Coin ICO
The Official Charity Sea Coin (CHRTY) ICO Contract

# The project uses:
1. Ethereum blockchain as a base of infrastructure
2. Truffle 4.1.3 for testing
3. OpenZeppelin v1.9.0 contracts as a base of source code

### Coin summary
1. Current Coin address: ``
2. Coin symbol: CHRTY
3. Coin decimals: 18

### Project summary
The project consists of ERC20 app Coin and crowdsale smart contracts for Pre-ICO and ICO.

`contracts/CharitySeaCoin.sol` contains CHRTY Coin smart contract. CHRTY is a capped Coin with an option to adjust its cap only once. The adjustment takes the current Coin supply and makes it equal to 6% of the cap (`cap = CoinSupply * 100 / 6`). This feature is supposed to be used after the pre-ICO for ratio preserving.

`contracts/BaseCharitySeaCoin.sol` contains the general functionality of the crowdsale (PreICO and ICO):
* It allows to set the ETHUSD and USDCHRTY rate (USDCHRTY can be set with 5 significant digits)
* Any payment less than `ETHER_THRESHOLD` will be rejected
* ETHCHRTY rate is defined as `ETHUSD / USDCHRTY`
* After the end of crowdsale the ownership of the Coin instance will be transferred to original owner.

`contracts/CharitySeaPreIco.sol` contains the Pre-ICO smart contract. After the end of Pre-ICO cap of CHRTY Coin will be adjusted as described earlier.

`contracts/CharitySeaIco.sol` contains the ICO smart contract. It adds the time bonuses feature, after finalization it distributes the Coins for the team, project and bounty and forbids any further Coin emission.

**IMPORTANT: for the proper work of the crowdsale smart contracts they need to take an ownership of the Coin instance. Use the** `Coin.transferOwnership()` **method in order to fulfill this requirement**
