# Geojam (JAM) With Liquidity Protection Service

##Details

---

#### Geojam (JAM) Protection parameters


User LiquidityProtectionsService address in the integrated token UsingLiquidityProtectionService.liquidityProtectionsService() override

    Current JAM LiquidityProtectionsService address: 0x80A703aD8f590035f2A18BD433a847694c83c069

Switch off protection automatically on Saturday, January 15, 2022 11:59:59 PM GMT

[comment]: <> (>Epoch timestamp: 1642291199)

---
#####FirstBlockTrap On
block all users who buy tokens in the same block with pair creation transaction

---

#####LiquidityAmountTrap On
    LiquidityAmountTrap_blocks 5
    LiquidityAmountTrap_amount 1 110 000
block every user who buys in total more than 1 110 000 tokens during the 5 first blocks after pair creation

---

#####LiquidityPercentTrap On
    LiquidityPercentTrap_blocks 6
    LiquidityPercentTrap_percent 4%
block every user who buys more than 4% of current liquidity in one transaction, limitation works during the 6 blocks

---

#####LiquidityActivityTrap On
    LiquidityActivityTrap_blocks 3
    LiquidityActivityTrap_count 8
will block all users who buy tokens if in the same block was more than 8 transaction, limitation works during the 3 blocks

---

###====================

## Installation

    npm install
    npm run compile

## Testing on fork

    npm run test -- --network hardhat

## Deployment

Set bsc network node url and deployer private key in the .env file.

    npm run hardhat -- --network eth deploy --owner 0xOwnerAddress

## etherscan verification

Set API key for etherscan in the .env file.
[https://etherscan.com/myapikey](https://etherscan.com/myapikey)

    npx hardhat verify --network eth 0xTokenAddress

## Usage

Unblock accounts (must be done while protection is still on):

    npm run hardhat -- --network eth unblock --token 0xTokenAddress --json ./blocked.example.json

Revoke tokens from blocked accounts (must be done while protection is still on):

    npm run hardhat -- --network eth revoke-blocked --token 0xTokenAddress --to 0xRevokeToAddress --json ./blocked.example.json

Disable protection to make transfers cheaper:

    npm run hardhat -- --network eth disableProtection --token 0xTokenAddress

Change the Liquidity Protection Service address:

    npm run hardhat -- --network eth changeLPS --token 0xTokenAddress --lps 0xNewLpsAddress

