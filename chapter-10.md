# Chapter 10: A Variety of Economic Mechanisms

# Stable Coins

Stablecoins are cryptocurrencies that are designed to be price-stabilized - i.e. minimal price volatility. Often, this is done by pegging to more stable assets or benchmark such as fiat dollars.

Despite the fact that the idea of a price-stable cryptocurrency has been around since 2013, volatility is still often cited as the bottleneck of innovation and wider adoption of cryptocurrencies. Businesses and consumers don’t want to be exposed to price volatility when transacting in cryptonetworks. How can you pay someone’s salaries in a currency that can fluctuate 20% in 24 hours? The ecosystem is in need of a stable currency that can be traded for goods or services in order to overcome this adoption barrior.

This is where stablecoins come in. Because they are deployed on top of blockchains, stablecoins retain the advantages of cryptocurrencies: natively digital, transferable, and decentralized. While stablecoins are currently commonly used by cryptoasset traders as a peg against market volatility, well-designed stablecoins have the potential to enable use cases that are uniquely enabled by blockchain technology - e.g. prediction markets and smart insurance.

In this chapter we will focus on the mechanisms in which stablecoins are created, along with examples of existing projects implementing each.

## Tradeoffs: The Stablecoin Trilemma

All projects in the Stablecoin space have been forced to choose two of these three characteristics to build
out their vision. Stablecoins suffer from their own trilemma where you can only have two out of the three desired states:

* Decentralization
-- How open the network is, no central authority, the variability of validators and distribution of confirmation power)
* Capital Efficiency
-- The stablecoin is backed with 100% collateral or less) and
* Collateralization
-- Occurs when a borrower pledges an asset as recourse to the lender in the event that the borrower defaults on the initial loan
  
## Fiat-collateralized Stablecoins

Fiat-collateralized stablecoins are backed by fiat reserves held by a custodian, typically a bank. The company issuing the coins deposit fiat dollars into the bank and issue stablecoins 1:1 against this reserve. When a user wants to liquidate the stablecoin back into fiat, the company destroys the coin and sends fiat dollars back to the user. 

Fiat-collateralization is the simplest stablecoin scheme. It is also the *most centralized* because users are inherently trusting the issuing company to maintain the collateral and keep promises of coin redemption. Stablecoins under this scheme can be seen as IOUs redeemable for fiat. This setup is subject to the same credit and counterparty risk that comes with any standard bank deposit. If a user wants to exit the stablecoin back to fiat, they are also subject to the costs, regulation, and transaction speed inherent to legacy payment rails.

Because the collateral is held in fiat reserves, a stablecoin issued under this scheme is most robust against cryptocurrency price fluctuations. It is also less vulnerable to hacks because the collateral is being held off-chain. Companies issuing stablecoins under this scheme can undergo regular public audits to demonstrate trustworthiness and transparency. They can also provide legal protection against misappropriation of the underlying assets. These additional steps, though responsible ones to take, do translate to added operational costs for the company.

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

Smart contracts mint TrueUSD when USD clears the escrow accounts, and burns TrueUSD when USD is redeemed. This ensures a 1:1 parity between the TrueUSD in circulation and USD in the escrow accounts. TrustToken plans to extend this model to other fiat currencies, precious metals, and even assets like stocks and real estate in the future.

Individuals and institutions must have a verified TrueCoin account and undergo KYC/AML proceedures in order to redeem TrueUSD for USD, exchanging directly with one of the escrow accounts in TrustToken's network of fiduciary and banking partners.

#### DigixGold

Digix is tokenizing gold ownership. DigixGold utilizes a dual-token system to represent stake ownership in DigixDAO,
the entity creating the tokens, and DGX, which is a fully-collateralized representation of vaulted gold. 1 DGX
token is equal to 1 gram of gold. There are fees associated with DGX in order to facilitate their Proof of Asset
protocol for Vendor, Auditor, and Custodian, which amounts to a 0.6% fee annually and a 0.13% transaction
fee.
Digix has multiple pending partnerships with other projects that require a stable on-chain collateral, such as
the Dai stablecoin, allowing gold itself as an asset to underlie and stabilize some of the algorithmic stablecoin
projects.

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

// TODO: price feeds, tradeoffs/risks, role of MKR token, governance

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
+ Capital efficient as it does not involve a collateral backing it

Many existing coins offer some form of incentive mechanism or dividend built into its design (e.g. seigniorage shares, voting rights, transaction fee dividends).

Cons:
- Most complex to design and audit
- Unproven monetary policy. Since there is no collateral to liquidate the coin back to there are dire consequences if the algorithms aren't well-designed (e.g. 'death spiral'*)
- Increased risk factor as users are giving up stablecoins of certain value in the present for uncertain value in the future. If the currency is not adopted, the price will not rise enough to generate enough stablecoins to pay out to shareholders
- Since increased demand is needed to drive up the coin price such that an increase in the money supply is required, the coin will not be able to maintain its peg if the network doesn't continue growing
- Low coin prices are handled by *promises of future growth*, which must be subsidized by buying into the scheme

* a ‘death spiral’ is where increasing amounts of shares must be sold to purchase and retire more coins, further lowering the price while massively increasing the outstanding shares. As the amount of unredeemed shares increases with this dilution, potential buyers are discouraged even as the stablecoin crashes to zero.

Because trust-creation is important in initial phases of a project (over decentralization), some stablecoin projects have started with an asset-backed token, with plans to eventually move to an algorithmic scheme. Here are some examples of algorithmic stablecoins:

#### Basis 

In its whitepaper, Basis described itself as the "price stable cryptocurrency with an algorithmic central bank". In its stablecoin protocol, smart contracts expand and contract the supply of Basis tokens in response to deviations of the trading price from its pegged asset. Theblockchain monitors the trading price of Basis tokens by sourcing Basis-USD exchange rates via an oracle, which can be done in a decentralized way.

Basis proposed a three-token system consisting of:

**Basis tokens**: the stablecoin designed to trade at a stable price peg. 

**Bond tokens** are created and auctioned off on the open market in the event that Basis trades below its peg. Users can purchase bonds with Basis in order to decrease the Basis token supply and thereby increase its price. Bond tokens cost less than 1 Basis and have the potential to be redeemed for exactly 1 Basis when Basis is created to expand supply, incentivizing speculators to participate in bond sales and destroy Basis in exchange for the potential that bond tokens will pay out in the future.

When Basis tokens return to and trade above the peg, the algorithm increases the money supply in order to bring the price back down, users can redeem their bond tokens for Basis. Bond tokens are not tradeable and can only be held until redemption or expiration.

The conditions for redeeming Basis with bond tokens are as follows:
- Basis is trading above its pegged and the algorithm has deemed money supply expansion to be necessary (i.e. it is creating and distributing Basis)
- All bond tokens that were created before this bond have been redeemed or expired: bond token holders can redeem their coins on a first-in-first-out (FIFO) basis. The older their bonds, the further forward in line they are to receive newly created newly minted Basis tokens. This mechanism serves to encourage buyers to act early in the face of a Basis coin decline and prevent a self-perpetuating decline in token price.
- This bond has not expired: all bond tokens have an expiration date of five years after its creation. This serves to prevent the bond queue becoming so large that it deters potential new bond token buyers from obtaining them

Basis bonds have a price floor of $0.10, below which bonds simply will not be sold. This was implemented in an effort to ensure against the worst-case scenario of massive dilution that would come from retiring coins with bonds sold for pennies on the dollar.

**Share tokens** are a fixed supply token whose value lies in its dividend policy. When all outstanding bonds have been redeemed and the Basis token continues to trade over par, additional Basis tokens are issued to share token holders pro rata. Unlike bond tokens, share tokens are not redeemed cand an theoretically receive unlimited Basis tokens as or if demand increases. Share tokens are not tradeable on public exchanges.

A hypothetical scenario under an **expansion** event (Basis trades below $1)
* Suppose there are 500 bonds in the Bond Queue, 200 of which were created more than 5 years ago. Additionally, suppose there are 1,000 shares in circulation.
* Suppose the system needs to create 1,000 new coins.
* The system expires the 200 oldest bonds, leaving 300 bonds in the queue. If the system needed to create fewer than 300 coins, it would only redeem the oldest bonds. However, the system needs to create 1,000 coins, so it redeems all 300 bonds.
* The system still needs to create 700 more coins. The system distributes these 700 coins evenly across the 1,000 shares. Each share receives 700 / 1,000 = 0.7 coins. If you hold 100 shares for example, you would receive 70 coins during this expansion, which you can then sell for USD.

A hypothetical scenario under an **contraction** event (Basis trades above $1)
* Suppose the system wants to sell 100 bonds.
* Suppose that there are three buy orders on the order book: One bid for 80bonds at 0.8 Basis each, one bid for 80 bonds at 0.6 Basis each, and one bid for 80 bonds at 0.4 Basis each.
* The system will compute the clearing price, which is a single price at which all offered bonds would have been bought at. Here, the clearing price is 0.6 Basis.
* The system will fill the winning bids at the clearing price: The first user will receive 80 bonds in exchange for 80 * 0.6 = 48 coins, and the second user will receive 20 bonds in exchange for 20 * 0.6 = 12 coins.

##### Regulations & The Fate of Basis
As of December 13 2018, Basis decided to shut down, citing primarily regulatory restrictions as impediments to its launch and network adoption. As regulatory guidances for cryptocurrencies came out, it became more apparent that Basis' bond and share tokens would have been characterized as securities. This would have subjected these tokens would to transfer restrictions, with the company being responsible for limiting token ownership to accredited investors in the US for the first year after issuance and for performing eligibility checks on international users.
These transfer restrictions would have significantly compromised censorship resistance and on-chain liquidty as it would have required the company to maintain a centralized whitelist of users. The whitelist would be required indefinitely as Basis' monetary policy involves continual issuance and redemption of bond and share tokens. 
Since the system's stability relies on its ability to auction off bond tokens in open markets, transfer restrictions would have significantly impaired this core mechanic.

Despite the disappointing outcome, Basis return capital to investors after being unable to find a compelling enough workaround to comply with regulations.

#### Carbon
Carbon is another example of a stablecoin designed under a decentralized seigniorage shares scheme. It is one of the first cryptocurrencies to build on Hedera Hashgraph. It utilizes a dual-token model which consists of:
1. Carbon stablecoin and 
2. Carbon Credit token (“Carbon Credit”)

When Carbon is trading under its $1 peg, Carbon Credits are auctioned off to market participants who are willing to burn their Carbon stablecoins. Carbon Credit holders are later rewarded when demand for Carbon stablecoins increase in the future, and the stablecoin trades above the $1 peg. When the price of Carbon stablecoin is above $1, the smart contract mints new stablecoins and distributes them to Carbon Credit holders on a pro-rata basis. This theoreticlaly will create downward pressure and push the price of the stablecoin back to its $1 peg.

Price Oracle
Every 24 hours, nodes submit bids for what they believe is the correct exchange rate for Carbon. Anyone who bids outside the 25th and 75th percentiles will have their balances deducted and given to the bidders whose bids fall within the 25-75th percentile. This may seem controversial and deter participation because it means that, evne if a node reports a price even *marginally* outside the 25-75th percentile, their balance would be deducted.

Unlike other Seignourage shares stablecoins, Carbon it allows users to freeze portions of their funds to manage contraction and expansion cycles. The Carbon system gives 100% of the upside to users who helped the system to contract through burning their tokens.

Carbon will launch as a hybrid (algorithmic/fiat-backed) token in Q2 2019

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

[1] Blockchain.com ["The State of Stablecoins 2018"](https://www.blockchain.com/ru/static/pdf/StablecoinsReportFinal.pdf). Retrieved 24 Jan 2019.

[2] Kade, Stephen. ["TrueUSD: A Stablecoin that you can redeem 1-for-1 for US Dollars"](https://blog.trusttoken.com/trueusd-a-usd-backed-stablecoin-you-can-trust-9688796cfd0d)

[3] Memon, Bilal. ["Guide to Stablecoin: Types of Stablecoins & Its Importance"](https://masterthecrypto.com/guide-to-stablecoin-types-of-stablecoins/). Retrieved 22 Oct 2018.

[4] Qureshi, Haseeb. ["Stablecoins: designing a price-stable cryptocurrency"] (https://hackernoon.com/stablecoins-designing-a-price-stable-cryptocurrency-6bf24e2689e5). Retrieved Feb 20 2018.

[5] Samman, George. ["The State of Stablecoins 2019
Hype vs. Reality in the Race for Stable, Global, Digital Money"](https://static1.squarespace.com/static/564100e0e4b08c9445a5fc5d/t/5c71e43ef9619ae6c83c30af/1550967911994/The+State+of+Stablecoins+2019_Report+2_20_19.pdf). Retrieved Mar 12 2019.

[6] Sams, Robert. ["A Note on Cryptocurrency Stabilisation: Seignourage Shares"](https://assets.ctfassets.net/sdlntm3tthp6/resource-asset-r390/5a940afb21681d19c0b3b76cf69259e1/58ebe9e2-1f28-4a8d-8ce1-26abef07aedf.pdf)
