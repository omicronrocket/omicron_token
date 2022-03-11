# Implemented Features
1. Presale using BNB
2. Marketing & Team wallet vesting
3. Redistribution & auto liquidity
4. Airdrop to holders

# How it works
## 0. Initial token Distribution
- 20,000,000,000 (20%) to Liquidity Wallet (0xfbcB5A5a96155d1A9229cac651884AB2730012f2)
- 275,000,000 (0.00275%) to Marketing wallet (0x78BfcA0C53Ac8e6eFDE1979079B516AC3B8B8CFb)
- 40,000,000,000 (40%) to BURN wallet (0xf081a6bcC50079E122a387043BBda1C50F8A9810)
- 225,000,000(0.00225%) to Team wallet (0xB7EF0e728a9b4714153c049c58d19f8a4fd0db9c)
- Rest moves to the dead address and locked for vesting, presale, and airdrop (0xA33F2F6EDf07db1F10984119d301aB2291687Dc3)

## 1. Presale
- Presale starts 17th of march, 13:00 CET (1647518400), ends 24th of March, 13:00 CET (1648123200). 
- Presale accepts BNB and a wallet can pay in range 0.05 ~ 150 BNB. A user should call the following function to participate.
```
participatePresale() 
```
This function gets BNB price in usd using pancakeswap and record how many tokens are purchased in presale for the caller. (1 OMIR = 0.001 USD). All BNBs are moved to predefined address:
```
address private FUND_WALLET = 0x01096559F1595Fad92646A2fED58048f9F611699;
``` 

- Presale participants can claim their purchase after 26th 13:00 CET (1648296000) using the follow function call.
```
function claimPresale() external 
``` 


## 2. Marketing & Team wallet vesting
Following wallets are used as Marketing and Team wallet. 
```
address public MARKETING_WALLET = 0x78BfcA0C53Ac8e6eFDE1979079B516AC3B8B8CFb;
address public TEAM_WALLET = 0xB7EF0e728a9b4714153c049c58d19f8a4fd0db9c; 
```
- Team, Marketing wallet unlock is started from 25th March 13:00 CET, every 30 days. 156,750,000 to market, 128,250,000 to team wallet each time. 
- Contract owner should call the following function to unlock.
```
function claimVest() external onlyOwner
```
- Unlock time, and amount limitations are present.

## 3. Redistribution & auto liquidity
This feature was implemented by forking Safemoon's math model. 

## 4. Airdrop
Airdrop starts 27th March 13:00 CET (1648382400), and exists for 100 days. 25% total supply will be airdropped for 100 days (1% each day).
- The following function should be called by the contract owner
```
function airdrop() external onlyOwner
```
- In this function airdrop amount of tokens are treated as tax fee and distributed to holders except team wallets.

    
