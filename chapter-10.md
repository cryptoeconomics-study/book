# Chapter 10: A Variety of Economic Mechanisms

# Stable Coins

Stablecoins are cryptocurrencies that are designed to be price-stabilized - i.e. minimal price volatility. Often, this is done by pegging to more stable assets or benchmark such as fiat dollars.

Despite the fact that the idea of a price-stable cryptocurrency has been around since 2013, volatility is still often cited as the bottleneck of innovation and wider adoption of cryptocurrencies. Businesses and consumers don’t want to be exposed to price volatility when transacting in cryptonetworks. How can you pay someone’s salaries in a currency that can fluctuate 20% in 24 hours? The ecosystem is in need of a stable currency that can be traded for goods or services that you can overcome this adoption barrier of volatility.

That’s where stablecoins come in. Because they are deployed on top of blockchains, stablecoins retain the advantages of cryptocurrencies — digital, transferable, and decentralized. While stablecoins are currently commonly used by cryptoasset traders to peg against market volatility, well-designed stablecoins have the potential to unlock other use cases of the blockchain (e.g. prediction markets, smart insurance).

In this chapter, we will focus on the mechanisms in which stablecoins are created along with examples of existing projects implementing them.
  
## Fiat-collateralized Stablecoins

Fiat-collateralized stablecoins are backed by fiat reserves held by a custodian, typically a bank. The company issuing the coins deposit fiat dollars into the bank and issue stablecoins 1:1 against this reserve. When a user wants to liquidate the stablecoin back to fiat, the company destroys the coin and sends fiat dollars back to the user. 

Fiat-collateralization is the simplest stablecoin scheme. It is also the most centralized because users are inherently trusting the issuing company to maintain the collateral and keep promises of coin redemption. Stablecoins under this scheme can be seen as IOUs redeemable for fiat. This setup is subject to the same credit and counterparty risk that comes with any standard bank deposit. If a user wants to exit the stablecoin back to fiat, they are also subject to the costs, regulation, and transaction speed inherent to legacy payment rails.

Because the collateral is held in fiat reserves, a stablecoin issued under this scheme is most robust against cryptocurrency price fluctuations. It is also less vulnerable to hacks because the collateral is being held off-chain. Companies issuing stablecoins under this scheme can undergo regular public audits to demonstrate trustworthiness and transparency. They can also provide legal protection against misappropriation of the underlying assets. These additional steps, though responsible ones to take, means additional operational costs for the company.

Pros:
+ Simplest, easy-to-understand mechanics
+ Most robust in terms of price stability
+ Least vulnerable to software failure as collaterals are held off-chain

Cons:
- Centralized, single point of failure — need a trusted custodian to store the fiat
- Counterparty risk & reliance on traditional banking system
- Lower transparency than on-chain collateralized systems - need regular public audits/attestations to escrowed funds
- Cumbersome liquidation process, constrained to legacy payment rails and regulations


#### TrustToken

TrustToken is a platform to create asset-backed tokens that users around the world can buy and sell. Their first asset token is **TrueUSD**, a stablecoin that users can redeem 1-for-1 for US dollars. TrustToken partners with registered banks and fiduciaries to directly handle and hold the funds backing TrueUSD tokens in an escrow account.

Smart contracts mint TrueUSD when USD clears the escrow accounts, and burns TrueUSD when USD is redeemed This ensures a 1:1 parity between the TrueUSD in circulation and USD in the escrow accounts. TrustToken plans to extend this model to other fiat currencies, precious metals, and even assets like stocks and real estate in the future.

Individuals and institutions must have a verified TrueCoin account and undergo KYC/AML proceedures in order to redeem TrueUSD for USD, exchanging directly with one of the escrow accounts in TrustToken's network of fiduciary and banking partners.

//TODO:
Examples of other projects with non-crypto-asset-backed stablecoins e.g. DigixGold

#### DigixGold

#### Federal Reserve
//TODO

- What mechanisms do the Federal Reserve use?

## Crypto-collateralized Stablecoins

Unlike fiat-backed stablecoins, crypto-collateralized stablecoins are backed with reserves of other cryptocurrencies such as BTC or ETH. Everything is on the blockchain and no fiat is required, making this mechanism more decentralized than the fiat-collateralized setup above. 

In this mechanism however, our collateral (other cryptoassets) can fluctuate in value. To prevent the stablecoin also fluctuating in value we must **over-collateralize** it in order to absorb price fluctuations in the collateral. If the price of the collateral drops enough, the stablecoins get liquidated. The issuance and liquidation of crypto-collateralized stablecoins is handled by the blockchain in a decentralized manner. 

This decentralization comes at a cost of capital-efficiency because of the need to over-collateralize. While a fiat-backed stablecoin will require only 100K collateral to issue 100K stablecoins, a crypto-collateralized coin might require 200K collateral or more to issue the same amount.

Pros:
+ More decentralized as the collateral is held on-chain
+ More transparent since anyone can observe the collateralization ratios at any time
+ Quick on-chain liquidation process into the underlying cryptoassets

Cons:
- Less price-stable than fiat-backed coins
- Affected by large fluctuations in other cryptocurrency(ies) - coins can get auto-liquidated in the event of a price cash
- More capital-intensive than fiat-backed coins due to the need to over-collateralize
- Reliance on accurate price feeds for cryptoassets backing the coin
- Very complex to design and audit: have yet to be tested by time, more users, and more price fluctuations

#### MakerDAO

MakerDAO's Dai is a USD-pegged stablecoin backed by ETH (and in the future, other cryptocurrencies). The system uses smart contracts to stabilize Dai’s exchange rate through the use of **Collateralized Debt Positions** (CDPs) and autonomous feedback mechanisms. This means that there are valuable assets held in smart contracts on the Ethereum blockchain that are available to buy back Dai, propping up the price and keep it stable at one dollar.

CDPs are collateralized smart contracts that allow users to generate Dai in proportion to the value of the deposited assets. A user deposits ether into the CDP smart contract, where it is held until the debt (as well as interest) is fully paid.  In order to combat the volatility of the underlying collateral, the Dai system can liquidate CDPs by auctioning off the underlying collateral held by the smart contract whenever the value of the collateral falls sufficiently.

// TODO: price feeds, governance, tradeoffs/risks, role of MKR token

## Seigniorage (Non-Collateralized/Algorithmic) Stablecoins

Historically, the term **seigniorage** refers to the profits that central banks and governments receive by minting new money. The Seigniorage Shares scheme was pioneered by Robert Sams in 2014 in a design proposal for **non-collateralized** stablecoins. Instead of holding fiat in reserve or have other cryptocurrencies back the coin, the scheme relies purely on smart contract(s) to ensure a stable trading price by running algorithms that autonomously control the coin supply. In other words, the smart contract acts as an "algorithmic central bank" whose only mandate is to issue a currency that trades at a stable price -- say $1.

In this scheme, smart contracts control the inflation/deflation of the stablecoin through a **shares-for-coins** and **coins-for-shares** mechanism. The *shares* represent a claim on the future value of coins to fulfill demand while the *coins* themselves act as a price-stable medium of exchange. Let's explore some scenarios:

**Stablecoin price is higher than intended peg**
If the stablecoin trades too high (i.e. supply is too low), the smart contract mints and auctions off new coins in exchange for shares. The inflation increases money supply, bringing down the price of the coin and decreases the number of shares, thus increasing the value of the shares. Issuing shares results in excess coins being distributed, leaving the smart contract with some extra profits (seignourage). 

**Stablecoin price is lower than intended peg**
If the coin is trading too low (i.e. supply is too high), the smart contract buys up coins on the market and deflates the circulating supply. 
However, if the smart contract's seignourage is insufficient to buy up enough coins, it can issue shares that entitle the buyer to *future* seignorage. This means that the next time it issues new coins and earns seignorage, shareholders will be entitled to a share of those profits. This predicates on the assumption that demand for the coin will increase in the future. Share buyers are expecting future seignourage in return for the coins they sell for shares now. Those who sell their stablecoins for shares enable the coin supply to decrease, restablizing the price to $1. The shares they hold now act as claims on future coin distribution as demand for the coin increases.

Pros:
+ No need for additional assets to back additional coin issuance
+ Most decentralized, digitally native and independent of fiat or any other cryptocurrency
+ Stronger network adoption incentive due to the (perceived) potentialto earn profits on the creation of stablecoins

Many existing coins offer some form of incentive mechanism or dividend built into its design (e.g. seigniorage shares, voting rights, transaction fee dividends).

Cons:
- Most complex to design and audit
- Unproven monetary policy. Since there is no collateral to liquidate the coin back to there are dire consequences if the algorithms aren't well-designed (e.g. a crash to zero)
- Increased risk factor as users are giving up stablecoins of certain value in the present for uncertain value in the future. If the currency is not adopted, the price will not rise enough to generate enough stablecoins to pay out to shareholders
- Since increased demand is needed to drive up the coin price such that an increase in the money supply is required, the coin will not be able to maintain its peg if the network doesn't continue growing
- Low coin prices are handled by *promises of future growth*, which must be subsidized by buying into the scheme

Because trust-creation is important in initial phases of a project (over decentralization), some stablecoin projects have started with an asset-backed token, with plans to eventually move to an algorithmic scheme. Here are some examples of algorithmic stablecoins:

#### Carbon

#### Basis 

// TODO
- What is Basis
- As of December 13, 2018, Basis has decided to shut down. Why did it fail?

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

[5] Kade, Stephen. ["TrueUSD: A Stablecoin that you can redeem 1-for-1 for US Dollars"](https://blog.trusttoken.com/trueusd-a-usd-backed-stablecoin-you-can-trust-9688796cfd0d)

[6] Sams, Robert. ["A Note on Cryptocurrency Stabilisation: Seignourage Shares"](https://assets.ctfassets.net/sdlntm3tthp6/resource-asset-r390/5a940afb21681d19c0b3b76cf69259e1/58ebe9e2-1f28-4a8d-8ce1-26abef07aedf.pdf)
