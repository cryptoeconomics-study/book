# Chapter 10: A Variety of Economic Mechanisms

# Stable Coins

Stablecoins are cryptocurrencies that are designed to be price-stabilized - i.e. minimal price volatility. Often, this is done by pegging to more stable assets or benchmark such as fiat dollars.

Despite the fact that the idea of a price-stable cryptocurrency has been around since 2013, volatility is still often cited as the bottleneck of innovation and wider adoption of cryptocurrencies. Businesses and consumers don’t want to be exposed to price volatility when transacting in cryptonetworks. How can you pay someone’s salaries in a currency that can fluctuate 20% in 24 hours? The ecosystem is in need of a stable currency that can be traded for goods or services that you can overcome this adoption barrier of volatility.

That’s where stablecoins come in. Because they are deployed on top of blockchains, stablecoins retain the advantages of cryptocurrencies — digital, transferable, and decentralized. While stablecoins are currently commonly used by cryptoasset traders to peg against market volatility, well-designed stablecoins have the potential to unlock other use cases of the blockchain (e.g. prediction markets, smart insurance).

In this chapter, we will focus on the mechanisms in which stablecoins are created along with examples of existing projects implementing them.
  
## Fiat-collateralized Stablecoins

#### Federal Reserve
//TODO

- What mechanisms do the Federal Reserve use?

## Crypto-collateralized Stablecoins

Unlike fiat-backed stablecoins, crypto-collateralized stablecoins are backed with reserves of other cryptocurrencies such as BTC or ETH. Everything is on the blockchain and no fiat is required, making this mechanism more decentralized than the fiat-collateralized setup above. 

In this mechanism however, our collateral (other cryptoassets) can fluctuate in value. To prevent the stablecoin also fluctuating in value we must over-collateralize it in order to absorb price fluctuations in the collateral. If the price of the collateral drops enough, the stablecoins get liquidated. The issuance and liquidation of crypto-collateralized stablecoins is handled by the blockchain in a decentralized manner. 

This decentralization comes at a cost of capital-efficiency because of the need to over-collateralize. While a fiat-backed stablecoin will require only 100K collateral to issue 100K stablecoins, a crypto-collateralized coin might require 200K collateral or more to issue the same amount.

#### MakerDAO

MakerDAO's Dai is a USD-pegged stablecoin backed by ETH (and in the future, other cryptocurrencies). The system uses smart contracts to stabilize Dai’s exchange rate through the use of **Collateralized Debt Positions** (CDPs) and autonomous feedback mechanisms. This means that there are valuable assets held in smart contracts on the Ethereum blockchain that are available to buy back Dai, propping up the price and keep it stable at one dollar.

CDPs are collateralized smart contracts that allow users to generate Dai in proportion to the value of the deposited assets. A user deposits ether into the CDP smart contract, where it is held until the debt (as well as interest) is fully paid.  In order to combat the volatility of the underlying collateral, the Dai system can liquidate CDPs by auctioning off the underlying collateral held by the smart contract whenever the value of the collateral falls sufficiently.

// TODO: price feeds, governance, tradeoffs/risks

## Seigniorage (Non-Collateralized/Algorithmic) Stablecoins

#### Basis 
//TODO

- What was the Basis Protocol?
- Why did it fail?

## Other Stable Coin Mechanisms
//TODO

Add in any other interesting mechanisms (if the projects are now defunct, why?)

## Criticisms
//TODO

- See Preston Byrne's anti-stablecoin pieces

# Decentralized Storage
How does traditional storage work?

What advantage does decentralized storage give us?

What security or efficiency tradeoffs must be made to decentralize it?

How do Sia and other decentralized storage projects work?

# Decentralized DNS

How does traditional DNS work?

# Namecoin
# ENS
# Handshake

--------

[1] Memon, Bilal. ["Guide to Stablecoin: Types of Stablecoins & Its Importance"](https://masterthecrypto.com/guide-to-stablecoin-types-of-stablecoins/). Retrieved 22 Oct 2018.
[2] Blockchain.com ["The State of Stablecoins 2018"](https://www.blockchain.com/ru/static/pdf/StablecoinsReportFinal.pdf). Retrieved 24 Jan 2019.
[3] Qureshi, Haseeb. ["Stablecoins: designing a price-stable cryptocurrency"] (https://hackernoon.com/stablecoins-designing-a-price-stable-cryptocurrency-6bf24e2689e5). Retrieved Feb 20 2018.
[4] Samman, George. ["The State of Stablecoins 2019
Hype vs. Reality in the Race for Stable, Global, Digital Money"](https://static1.squarespace.com/static/564100e0e4b08c9445a5fc5d/t/5c71e43ef9619ae6c83c30af/1550967911994/The+State+of+Stablecoins+2019_Report+2_20_19.pdf). Retrieved Mar 12 2019.

