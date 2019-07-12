# Liquid Accommodation Supplements

## Team

[ligi](https://ligi.de) ([email](ligi+windingtree@ligi.de) | [github](https://github.com/ligi))

With a lot of help and on-site bug-fixes by [@thibmeu](https://github.com/thibmeu) from the liquidity.network

## Github repository of the project

[LiquidAccommodationSupplements on github](https://github.com/ligi/LiquidAccommodationSupplements)

## Description

Easily pay for supplements to your accommodation with the help of the liquidity.network after booking with winding-tree.

## Problems

When staying in ho(s)tels you often need pay for supplements (e.g. renting a bike, doing laundry, staying one more night, buying food ..). Especially in hostels this means you often have to reach for your wallet and deal with clumsy fiat-transfers or leak metadata and hurt your privacy by e.g. using credit cards.

## Solution

The solution this problem is that you have the Ethereum address of an ho(s)tel anyway after booking with [winding-tree](https://windingtree.com) (not currently part of their API - but as far as I understood, by talking to the team, this is coming in the future) - so I can just pull out my phone and quickly sign a transaction instead of having to bother with clumsy old school payment methods. In order of having a better user experience, less clutter on the main chain, more privacy and less transaction costs I want to leverage off chain transactions for this. I also wanted to use the chance to get familiar with the [liquidity.network](https://liquidity.network) as they are present and mentoring at the hackathon where this project was initiated.

The initiation of the project is an Android app that displays different options for accommodation supplements. And depending on what the user chooses: it shows a [liquidity.network](https://liquidity.network) QR-Code so the user can pay for it quickly.

The idea is that this app could be installed in the ho(s)tel on a tablet mounted somewhere.

Ideally at some point accommodation supplements (btw.: if someone has a better name for this please shoot) are part of the [winding-tree](https://windingtree.com) API. This way you might not even have to use a QR-Code but could directly do it from a booking app (which currently makes no sense to create as the search and booking API is not yet present).

## We learned

Winding-Tree and liquidity.network and are both very promising, but both in early stages of development. Unfortunately my initial plan to integrate liquidity.network in [WallETH](https://walleth.org) (the native Android Ethereum wallet I maintain) is not yet feasible as liquidity.network does not *yet* want other wallets to support it and actively prevents it from happening.

Liquidity.network does not yet support ERC-20 - but will do it very soon. After it supports it we should switch from using ETH to a stable ERC-20 token like DAI. I am pretty sure host will not be happy with the volatility of ETH and so not really happy about taking payments this way (but it is OK for the PoC).

Currently settling an invoice from Pending->Confirmed on the liquidity.network takes quite long - but this is also something that will change in the future.

The "Institute of Cryptoanarchy" is a nice place to hack :-)

## Extra resource

Here the links to the challenge(s) I accepted: [#10](https://github.com/windingtree/wt-hackathon/issues/10) alongside [#4](https://github.com/windingtree/wt-hackathon/issues/4)

## Credits

Thanks to [@thibmeu](https://github.com/thibmeu) for fixing issues I found ([#5](https://github.com/liquidity-network/liquidity-sdk/issues/5), [#6](https://github.com/liquidity-network/liquidity-sdk/issues/6)) on-site and being very helpful in providing information about the liquidity.network
