# Charity-Sea-Coin
The Official Charity Sea Coin (CHRTY) ICO Contract

# Usage

Ethereum blockchain as a base of infrastructure
Solidity 4.1.3 for testing
OpenZeppelin v1.9.0 contracts as a base of source code
Token summary
Current token address: 
Token symbol: CHRTY
Token decimals: 18
Project summary
The project consists of ERC20 app token and crowdsale smart contracts for Pre-ICO and ICO.

contracts/CHRTYSeaCoin.sol contains CHRTY Sea Coin smart contract. CHRTY is a capped token with an option to adjust its cap only once. The adjustment takes the current token supply and makes it equal to 6% of the cap (cap = tokenSupply * 100 / 6). This feature is supposed to be used after the pre-ICO for ratio preserving.

contracts/BaseCharitySeaCoin.sol contains the general functionality of the crowdsale (PreICO and ICO):

It allows to set the ETHUSD and USDCHRTY rate (USDMNR can be set with 5 significant digits)
Any payment less than ETHER_THRESHOLD will be rejected
ETHCHRTY rate is defined as ETHUSD / USDCHRTY
After the end of crowdsale the ownership of the token instance will be transferred to original owner.
contracts/CHRTYPreIco.sol contains the Pre-ICO smart contract. After the end of Pre-ICO cap of CHRTY token will be adjusted as described earlier.

contracts/CHRTYIco.sol contains the ICO smart contract. It adds the time bonuses feature, after finalization it distributes the tokens for the team, project and bounty and forbids any further token emission.

IMPORTANT: for the proper work of the crowdsale smart contracts they need to take an ownership of the token instance. Use the token.transferOwnership() method in order to fulfill this requirement
