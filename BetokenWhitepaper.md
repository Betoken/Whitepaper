# Betoken Whitepaper Draft

A meritocratic hedge fund built on the Ethereum blockchain.

## Authors

Zebang (Zefram) Liu, Guillaume Palayer

Contact: hello@betoken.fund

## Introduction

Betoken is a decentralized hedge fund built on the Ethereum blockchain that invests in ERC20 tokens. It automatically redistributes control over investment decisions to managers who make the most profitable investments. This collected wisdom is compiled into good investment decisions, using a unique decision making system we call "Incentivized Meritocracy".

The core ideas behind Betoken's Incentivized Meritocracy are:

* The control over decisions is tokenized.
* The control tokens are valuable.
* Good decisions are rewarded with control tokens proportional to both the quality and the quantity of their benefits.
* Bad decisions receive penalties in control tokens proportional to both how bad of a decision they were and how much damage they caused.

Betoken is for everyone: everyone can join, everyone can invest, everyone can make decisions for the fund and be rewarded for making good ones. And everyone can rise to the top if they have the merit.

Betoken is unstoppable: it is a completely decentralized application built on the censorship-resistant Ethereum blockchain.

Betoken is transparent: all statistics and decisions are publically available, and all fees and clauses are written in immutable open-source smart contracts.

Betoken will make investing in crypto-assets as simple as deposit-and-profit. Research and due diligence will be done by managers in the investors' stead, all with minimal need for trust between anyone.

Besides serving as a fund, Betoken will facilitate the collection, consolidation and sharing of data for reporting, risk management and supervisory purposes.

## 1. The Betoken Model

### 1.1 Incentivized Meritocracy

An **Incentivized Meritocracy** is a system where

* The amount of control each actor has is proportional to their ability to make good decisions.
* Actors are financially incentivized to maximize their control (therefore their decision-making ability).

The above definition is not rigorous, since "control" and "ability to make good decisions" are not clearly defined, but it provides a general idea of how an Incentivized Meritocracy should behave. To sum it up in one sentence: the best people are in charge, and everyone wants to be in charge. The first point is the desired result, and the second point is the means of achieving it.

Having the people with the most merit in charge is clearly good for an organization as a whole. In a hedge fund like Betoken, having the people who are the best at making investments handle the fund's investments means that the ROI (Return On Investment) of the fund is going to be of a high standard.

Incentivized Meritocracies have never been successfully implemented before, since it is near impossible to have a centralized actor that can judge everyone impartially. However, newly-invented smart-contract-enabled blockchains such as Ethereum allow us to construct **decentralized** actors that can uphold unbreakable rules, making implementing an actual Incentivized Meritocracy possible. Betoken is the first decentralized application that incorporates an implementation of Incentivized Meritocracy.

---

**Important Note: **The rest of Section 1 will be a high level description of Betoken's implementation of Incentivized Meritocracy. It will only be within the context of the Betoken hedge fund, rather than a generalized Incentivized Meritocracy. 

However, a formal and generalized description of Incentivized Meritocracies, as well as proof that Incentivized Meritocracies are indeed able to optimize the system's value, has been written. It can be found here: https://github.com/Betoken/documents/blob/master/Incentivized%20Meritocracies/Incentivized%20Meritocracies.pdf

---

### 1.2 Betoken's Solution

There are four central ideas behind Betoken's solution to Incentivized Meritocracy:

1. Control is denoted using Kairo (KRO) — Betoken's custom ERC20 token — that must be staked when making investments for the fund, and the amount of the stake is proportional to the amount of investment.
2. The control token KRO is valuable, in that holders of the token can expect income proportional to the amount of KRO they hold.
3. Good investment decisions are rewarded with KRO proportional to both the quality (ROI) and the quantity (profit / prevented loss) of the investment decision.
4. Bad investment decisions receive penalties in KRO proportional to both how far below 0 the ROIs were and how much money they lost.

We provide below a description of how Betoken functions and details of Betoken's Incentivized Meritocracy.

---

The Betoken fund runs in investment cycles, and at the start of each cycle there is a period of time where investors can deposit & withdraw their funds. When a user deposits $X$ Ether, they are given some amount of *Betoken Shares*, a custom ERC20 token, the amount of which is determined by the following equation:

* $shares = \frac{X}{totalFunds} \times totalShareSupply$

When they withdraw $X$ Ether, they have to burn some of their shares, the amount of which is determined by the same equation. During the first cycle, when there's no money in the fund, we simply use:

* $shares = constant \times X$

After the deposit & withdraw period, managers can start making investment decisions for the fund by staking some Kairos — the name we use for control tokens. Decisions are immediately turned into actual investments using the equation

- $investmentAmount = totalFunds \times \frac{decisionStake}{totalKairoSupply}$

During the decision-making phase, managers can also sell any asset they invested in whenever they want at the current market price. After an asset has been sold, the fund's smart contract automatically determines how profitable the investment was and rewards/takes away Kairo based on the results. The amount of Kairos a user gets back after selling an asset is $stake \times (1 + ROI)$, so if one of your investments had a 20% ROI, you would get 20% more Kairos back.

All investments should be sold before the end of the decision-making phase, or one's staked Kairos would be lost.

After the decision-making phase is over, a certain proportion (20%) of total profits is set aside as commission and distributed among Kairo holders proportional to the amount they hold. A certain proportion of fund assets (0.2%) is also sent to Betoken's developers as a fee to ensure platform maintenance and future developments.

### 1.3 Additional Reasons of Why Betoken Will be Successful

While we do have a [formal proof](https://github.com/Betoken/documents/blob/master/Incentivized%20Meritocracies/Incentivized%20Meritocracies.pdf) that Betoken's Incentivized Meritocracy will optimize the fund's profits, we feel it best to provide some additional reasons of why Betoken will be successful that are more intuitive and more closely related to reality. They will be laid out below.

#### 1.3.1 Better Than Direct Investment

To be able to attract people with flair in investing, we must make participating in Betoken's investment process more lucrative than directly investing in the tokens oneself. Fortunately, it is easy to prove that the model satisfies this requirement (discounting the fluctuation of Kairo's price):

* $ROI_{Betoken} = ROI_{Direct Investment} + \frac{commission}{investmentAmount} \geqslant ROI_{DirectInvestment}$

Therefore, managers are incentivized to join Betoken and make investment decisions.

#### 1.3.2 Analogous to Markets

Betoken's Incentivized Meritocracy shares many similarities to markets of investable assets, such as the stock market and the cryptocurrency market. In fact, staking in an investment decision is almost exactly the same as directly investing the token, except that the ROI is better. Therefore, we can estimate Betoken's success as a meritocracy by looking at how meritocratic the stock market and other markets currently are.

To our knowledge, there is no evidence that they are not meritocratic: no one's heard of a dumb and inexperienced investor besting market growth, and smart people (like those at Renaissance Technologies) have achieved amazing ROIs (71.8% annual on average! [[source](https://en.wikipedia.org/wiki/Renaissance_Technologies)]). Thus, we can expect that Betoken will also be meritocratic.

#### 1.3.3 Friendly to Beginner Managers
Since the launch of our Testnet Alpha, some people have told us that they haven't had time before to do their due diligence researching and accumulating knowledge about the best crypto-assets, but want to get better at it. Betoken offers beginner managers a safe environment to grow, since they can first observe how veteran managers make investments and let the community handle the fund's money, before dipping their toes into making decisions for an already full-fledged hedge fund.

Compared to ICONOMI and Melon, where you have to bootstrap a new hedge fund completely on your own, Betoken is much more beginner-friendly. It's the difference between getting a job at a well-established company and starting your own company. This trait facilitates the inflow of new managers into the Incentivized Meritocracy, which is essential to keeping Betoken's model effective in making decisions.

#### 1.3.4 Reduction of Operational Costs
Crypto fund managers and individual investors will become ultra-aware and over-burdened by one major painful oversight: operations. The process of buying, selling and storing cryptocurrency is not for the light hearted. There’s managing exchanges and OTC partners, setting up digital wallets, ensuring a foolproof custody process and tracking activities.

If you want a portfolio of 10 cryptoassets, it would take a couple of hours at least to just execute that portfolio. If you sign up for a centralized exchange on day 1, you have 100 ETH and want to put 10 ETH in 10 assets, that’s a three-hour process of signing up on exchanges, purchasing assets, registering your identity, actually getting your ethers, transferring your ethers, waiting for however long it takes for confirmation, then trading on a crypto-to-crypto order book, and then having to pull all those off the exchanges if you want to be secure.

This requires focus, time, energy, patience and resources. Fantasies of patient, thoughtful investing will be obliterated by the grind of producing tax-tracking spreadsheets and digital wallet management. It’s a complete disaster from a user experience perspective. Betoken will focus on making investing in crypto as simple as deposit-and-profit, so that research and due diligence is done by managers in their stead. Betoken’s users just instantly gain exposure to a portfolio of cryptoassets. It’s way easier.

We expect a wave of third party resources to service the funds and individual investors that want to stay in business. We want to be part of this new wave of services by **automating the whole buying, selling and reporting process**. Facilitating the collection, consolidation and sharing of data for reporting, risk management and supervisory purposes is also one of the potential key benefits of Betoken.

### 1.4 Potential challenges

#### 1.4.1 The Existing Regulatory Framework

Existing regulations do not provide an appropriate framework to existing and future blockchain projects and should not be applied to those projects as-is.

The regulatory wait-and-see policies represent a significant obstacle. Simple things such as the choice of company’s location or the fact that at any time, a directive or a legal decision can make your activity illegal.

Betoken aims to evolve quickly if the framework and rules are updated by the regulators. The use of blockchain technology in the markets induces a change of paradigm. Since the development of blockchain-based “disintermediation” exchanges, the current regulatory regime appears to be ill-suited to facilitating growth and innovation in the Fintech community.

More details about the constraints of applying a blockchain technology to finance can be found here: https://www.esma.europa.eu/sites/default/files/library/dlt_report_-_esma50-1121423017-285.pdf.

#### 1.4.2 Approval, Licensing and Operating Requirements

Betoken could need to get an approval and licensing from a national regulator, according to specific requirements in terms of operating rules, organizational structure, and human and material resources.
Once authorized, Betoken could be subject to a certain number of organizational rules, market surveillance and conduct requirements, in order to ensure that the markets are fair, transparent and efficient places, and to provide customer protection.

#### 1.4.3 KYC and AML Compliance

On the question of fraudulent activities and AML (Anti-Money Laundering), a robust governance would ensure that only trustworthy participants are accepted. In addition, the Ethereum network would allow for more transparency on transaction history and beneficial owners, which would enhance KYC (Know Your Customer) and help trace and prevent fraud.

#### 1.4.4 Tax Burden

Some challenges could also arise from the transnational nature of the blockchain. For example, a tax may apply on a given transaction depending on its place of execution. The law applicable to blockchain networks should be specified in advance to avoid conflicts.

#### 1.4.5 Operational risks

A mistake in the coding of smart contracts or reference data might affect a great number of participants. What would happen if the external data are flawed or become unavailable?

#### 1.4.6 Interoperability

Supporting cross-chain crypto-asset investment will be a major opportunity for Betoken. Solutions are emerging to handle this issue in the near future (Polkadot, Cosmos, KyberNetwork).

## 2. Implementation Details

### 2.1 Bootstrapping

#### 2.1.1 Kairo's Initial Distribution

We have decided to use a two-phase ICO as the means of distributing Kairo to the public.

* Stage 1: Before the Mainnet Pilot, we will distribute Kairo to early adopters who want to play with and help us test the Mainnet Pilot.
* Stage 2: Before our final release, we will do a second coin offering to facilitate a wider distribution of Kairo.

We understand that there has been vitriol towards ICOs in the crypto community, so we'd like to provide some justification for it.

* We have considered giving out Kairo for free when investors deposit during the first investment cycle. However, we want Kairo to be in the hands of users who actually want to make decisions for the fund, as it maximizes the effectiveness of Betoken's Incentivized Meritocracy. Giving Kairo to investors who want the community to manage their funds for them goes against this goal. Doing an ICO can help ensure that most of Kairo holders actually want to participate in the fund's decision-making process.


* It provides us with the funding we need to make progress in the technical and community development.

#### 2.1.2 Initial AUM Threshold

In order to make sure that there will be enough commission to let the Incentivized Meritocracy be self-sustainable, we will set an AUM (Asset Under Management) threshold in the first investment cycle.

### 2.2 Cycle Phases

Each cycle is divided into 3 phases:

* Deposit & Withdraw: When investors deposit and withdraw their funds.
* Make Decisions: When managers stake Kairo to make investments for the fund.
* Redeem Commission: When Kairo holders can redeem their commission. The Kairo smart contract is "paused" before the start of the next cycle (to prevent redeeming commission multiple times using the same tokens).

In a preliminary setup, the lengths of each phase are as follows:

* Deposit & Withdraw: 1 day
* Make Decisions: 28 days
* Redeem Commission: 1 day

Totaling 30 days.

For the functions that transitions the fund to the next phase, the successful caller can get a reward in Kairo. (similar to Ethereum Alarm Clock)

### 2.3 Token Exchange

Betoken uses Kyber Network as the token exchange platform for executing all of its investments.

KyberNetwork is "an on-chain protocol which allows instant exchange and conversion of digital assets (e.g. crypto tokens) and cryptocurrencies (e.g. Ether, Bitcoin, ZCash) with high liquidity."[[source](https://home.kyber.network/assets/KyberNetworkWhitepaper.pdf)] The inclusion of KyberNetwork can minimize the number of moving parts in Betoken's operation and significantly reduce Betoken's attack surface, reducing Betoken's running and maintenance costs and increasing its security.

### 2.5 Smart Contract Maintenance

#### 2.5.1 Upgrading Contracts

To upgrade the **BetokenFund** smart contract, the following steps will be taken:

1. The old contract is paused before the Waiting phase of the current cycle, and all users withdraws their investments.
2. The new contract is deployed.
3. The owner of the subcontracts (**ControlToken**, **ShareToken**) is set to the new contract.
4. The upgrade is now complete.

The script to do this can be found in Betoken's GitHub repository.

#### 2.5.2 Handling Emergencies

The **BetokenFund** contract inherits the **Pausable** contract from OpenZeppelin, so that it is possible to pause the normal operation of the fund when an emergency occurs, such as an attack or a market black swan event. When paused, an emergency withdraw function will be able to be called by users to withdraw all funds.

One thing to note about the emergency withdraw function is that if the fund is paused when the fund is invested in tokens, things would get more complicated, since the tokens have to be sold before users can withdraw, and the amount they can withdraw would likely be different from the amount at the start of the cycle.

#### 2.5.3 Contract Administrator

The **BetokenFund** contract inherits the **Ownable** contract from OpenZeppilin, and the owner is given administrator rights. Calling the emergency functions, pausing and unpausing, calling the functions related to upgrading, and changing the fund's fee rates all require administrator rights. Initially, the owner is set to be an account owned by the Betoken team, so that Betoken may be smoothly bootstrapped; after Betoken has enough community support, it is possible to set up a DAO (Decentralized Autonomous Organization) contract as the owner of Betoken, so that Betoken is completely decentralized.

### 2.6 Governance

As we mentioned in 2.5.3, the control over Betoken's smart contracts will initially be held by our team, until the Betoken community is large enough to sustain itself, after which a DAO will be set up as the contracts' owner. We are still considering different options for how the DAO will operate, and will list them out below.

#### 2.6.1 Votes

There are two options for what to use as votes in the DAO: one's Kairo balance and one's Betoken Shares balance. Both of them are viable, since the interests of Kairo holders and investors of the fund are all aligned with the interests of the entire fund. However, the two choices do have subtle differences.

##### 2.6.1.1 Reasons to Choose Kairo

* Using Kairo as votes would add additional value to Kairo tokens, benefiting the Incentivized Meritocracy.
* Kairo holders are likely more involved in the fund's operations than investors, which means they would know better about what's best for the fund, and would have a higher participation rate.

##### 2.6.1.2 Reasons to Choose Betoken Shares

* It makes sense to distribute power based on the stake one has in the fund. If someone has invested a lot in Betoken, they would expect to have a big say in administrative decisions.
* More secure to attacks. Even though extremely unlikely, it is possible for an attacker to spread FUD (Fear, Uncertainty, Doubt) so well that the price of Kairo drops significantly, buy in tons of Kairo, and take over the fund. The same is more difficult to accomplish with Ether: if you cause a lot of people to withdraw everything from the fund, and then deposit a ton of Ether yourself, you would actually reassure investors that it's still safe and well to invest in Betoken, counteracting your attack.

There is a third option where both Kairo and Betoken Shares are used as votes, which seems more reasonable than using either one individually, since both investors and managers will be represented in administrative decisions. This is the option we're considering to use.

#### 2.6.2 Implementation

We intend to use an established framework, such as Aragon, to implement the DAO.

## 3. Market Analysis

### 3.1 Competitors

Betoken faces two types of competition: competition for investors, and competition for managers. We will discuss them below.

#### 3.1.1 Competition for Investors

Since Betoken invests solely in cryptocurrencies, our customer base is different from that of traditional hedge funds that invests in stocks and bonds. Specifically, our customer base will mainly consist of open-minded accredited investors and individual cryptocurrency investors. There are two types of competitors for this customer base:

* Traditional hedge funds that have included cryptocurrencies as a new investment option.
* (Partly-)Decentralized cryptocurrency hedge fund platforms, such as ICONOMI and Melon. ICONOMI and Melon are both platforms where users can build their own traditional-style hedge funds that invest in cryptocurrencies. They do appeal to the same customer base as Betoken, but the fund managers on their platforms each keep their own information and investment strategies, whereas Betoken is able to combine the skills and resources of its managers for the good of the fund.

To investors, only two metrics have significance: risk and ROI.

* Betoken is definitely going to be riskier than traditional hedge funds. Compared to other decentralized hedge funds, Betoken's risk is on the same order of magnitude.
* Betoken's ROI mostly depends on the effectiveness of its Incentivized Meritocracy, which we cannot estimate at this point.

Therefore, the intensity of competition that Betoken will face largely depends on its ROI.

- If it is significantly better than anything else, then great. None of the competitors mentioned above will be relevant. Copycats may emerge, but network effect and first mover advantage will keep Betoken at the top.
- If it is on the same level as the aforementioned competitors, then Betoken will go head to head with ICONOMI and Melon, both of which will already have been launched for a long time when Betoken launches. Competition will be fierce, but Betoken will hold its place as the only crowdsourced cryptocurrency hedge fund.

#### 3.1.2 Competition for Managers

There are several competitors in this area:

* ICONOMI and Melon are platforms that allow managers to create their own hedge funds with customizable rules. The freedom of customization may appeal to some managers, but it comes with its own downside: you'd have to bootstrap a fund---its investment methods, its customer base, its reputation, etc.---from scratch if you join their platform. On the other hand, new managers in Betoken will be able to immediately start working for a full-fledged fund. It's the difference in difficulty between starting your own company and getting a job at an established company.
* Numerai is a hedge fund that uses an interesting auction system that lets data scientists compete to provide the best algorithms for predicting stock prices. The top rated algorithms will be used to make investment decisions for the hedge fund. [[source](https://numer.ai/whitepaper.pdf)] Numerai's model is inferior to Betoken's almost in every respect, because
  * In Betoken, the commission managers get is proportional to the size of the fund's assets, while the same is not necessarily true in Numerai.
  * The bets data scientists make in Numerai have binary results: either you lose all of your staked tokens or you lose none. In contrast, decisions in Betoken have much more granular results. This makes Betoken appeal better to risk-averse managers.
  * Numerai's model rewards algorithms that fit past data best, rather than algorithms that will perform well in real investment decisions, so there's a gap between the model's optimization goal and the actual goal. Betoken's model, on the other hand, rewards managers who **actually make the best decisions/most profit**.
  * There is a steep learning curve for joining Numerai as a manager, while all you have to do to start making decisions for Betoken is getting some Kairo.
* Quantopian and Quantiacs are crowdsourced hedge funds using similar but slightly better models compared to Numerai:
  * Users enter their algorithms in trading competitions, and the best algorithms are used for actual investing.
  * There's no staking or betting involved; anyone can enter competitions at no cost.
  * Algorithms don't have to use machine learning, so managers don't have to be data scientists.
  * The algorithms come in the form of trading bots, so they're far more connected to actual trading than Numerai's machine learning algorithms.
  * Developers of winning algorithms actually get a cut of all profits generated by their algorithms.

Since one manager can make decisions for as many hedge funds/platforms they like, competition for managers probably won't be as fierce as that for investors. However, we believe that Betoken will be the prime choice for the vast majority of managers. We list out below the pros and cons of joining Betoken from the perspective of managers.

##### 3.1.2.1 Pros for Choosing Betoken as a Manager

* Low barrier of entry. No need to learn a specific language, API, or type of algorithm, or even anything about programming; all you need to do is get some Kairo and start making decisions.
* No bootstrapping effort needed. New managers in Betoken will be able to immediately start working for a full-fledged fund, rather than having to bootstrap a fund by themselves.
* Higher returns. The ROI for making decisions in Betoken is even higher than that of directly investing into the tokens, and the commission you get is proportional to the fund's assets. No middleman taking away a large portion of your profits for no good reason.
* Automation: Betoken will automate the whole buying, selling and reporting process. See part 1.3.4 Reduction of operational costs.

##### 3.1.2.2 Cons for Choosing Betoken as a Manager

The parameters used in the fund, such as commission rates, cannot be changed by the will of a single manager, so if a manager wants full freedom in selecting such parameters alternatives like ICONOMI and Melon would be better.

### 3.2 Demand for Decentralized Cryptocurrency Hedge Funds

#### 3.2.1 Demand from Investors

One of Betoken's competitors, ICONOMI, has seen rapid growth in user count and book value. Quoting ICONOMI's [Q4 2017 Financial Report](https://medium.com/iconominet/iconomi-financial-report-q4-2017-17da25349f3d):

> Our user base increased more than 50% in the last quarter, and **in January we added more than 10,000 new users**. Our book value increased to \$327 million USD, which is 173% more than in Q3. But even more important than book value is the revenue the platform is generating. **DAAs have** **generated over \$200,000** **in revenue in one quarter**, an increase of more than four times over Q3.

From this evidence, it is clear that the demand for decentralized cryptocurrency hedge funds is real and fast growing.

If we look at cryptocurrency hedge funds in general, the numbers are even more promising: according to [Morgan Stanley](http://www.businessinsider.com/morgan-stanley-on-financial-institutions-interest-in-bitcoin-2017-12), investors have put over **$2 billion USD** into hedge funds specialized in cryptocurrency investments in 2017, and 2018 will likely be bigger.

The latest estimate of the number of crypto funds is 226 at the beginning of 2018, with $3.5 - 5 billion in assets under management [[source](https://next.autonomous.com/cryptofundlist/)]. 2018 could be on the same order of magnitude as 2017. And according to the [Eurekahedge Crypto-Currency Hedge Fund Index](http://www.eurekahedge.com/Indices/IndexView/Eurekahedge/682/Eurekahedge_Crypto_Currency_Hedge_Fund_Index), we’ve witnessed a 1,708.49% return for the 9 best crypto funds in 2017. With this kind of performance, we could witness a massive influx of new investors in the next months.

#### 3.2.2 Demand from Managers

There is evidence that quants and data scientists are interested in participating in hedge funds.

- According to Quantopian's [website](https://www.quantopian.com/about), over 700,000 algorithms have been submitted to their platform throughout its lifetime.
- According to a Wired [article](https://www.wired.com/2016/12/7500-faceless-coders-paid-bitcoin-built-hedge-funds-brain/), over 7,500 data scientists joined Numerai's competitions in 2016.
- The market cap for the ICONOMI token, which will be used for creating hedge funds on ICONOMI's platform [[source](https://iconomi.zendesk.com/hc/en-us/articles/115002851065-ICN-token)], is currently over $156 million USD. (Coinmarketcap, Feb 8 2018)

## 4. Road map

### Jan 2018
* MVP
* Landing page
* Testnet Alpha

### Feb-March 2018
* UI & UX improvements
* Further smart contract development
* Internal contract audit & testing
* Incentive model analysis & adjustments

### Q2-Q3 2018
* Whitepaper 1.0
* Legal consulting & paperwork
* Expanding Incentivized Meritocracy to other applications
* Testing Incentivized Meritocracy in existing organizations
* Third-party smart contract audits
* Customer research & community outreach

### Q4 2018
* Mainnet Pilot
* Official release

## 5. The team

### 5.1 Core members

#### Zebang (Zefram) Liu

Zefram is the cofounder and lead developer of Betoken. He currently studies Computer Science at UC San Diego. He is passionate about crypto-economics and mechanism design.

#### Surya Krishnan

Surya is the cofounder and incentive researcher of Betoken.

#### Guillaume Palayer

Guillaume is the cofounder of Betoken. His mission is to design and code the front end experience of the dApp. He's also an user researcher passionate by the token economy and the decentralized Web.

### 5.2 Advisors

## 6. Acknowledgement

We thank our friends, namely ..., ... for their feedback on the earlier version of this paper.
