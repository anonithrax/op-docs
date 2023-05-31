---
title: FAQs
description: Frequently Asked Questions about Ocean Protocol
---

# FAQ

Have some questions about Ocean Protocol?

Hopefully you'll find the answers here! If not then please don't hesitate to reach out to us on [discord](https://discord.gg/TnXjkR5) - there are no stupid questions!

### General Questions

<details>

<summary>What is a decentralized data marketplace?</summary>

A data marketplace allows providers to publish data and buyers to consume data. Unlike centralized data marketplaces, decentralized ones give users more control over their data, algorithms and analytics by minimizing custodianship and providing transparent and immutable records of every transaction. With features such as Compute-to-Data (C2D), data and algorithms can be ingested into secure Docker containers where escapes avoided, protecting both the data and algorithms.

</details>

<details>

<summary>What is needed to use a decentralized marketplace?</summary>

Users access decentralized marketplaces via Metamask. Metamask is an applet interface that manages unique IDs, generated and controlled fully by the user. These unique IDs (aka Ethereum address) are used to store digital assets such as cryptocurrency, datatokens, NFTs and other web3 native assets.

A Metamask wallet can easily be set up as a browser extension by going to your browser’s web store for extensions and search for “MetaMask”. For additional help setting up your MetaMask wallet, watch our short tutorial video and review these instructions on Ocean’s documentation page.

Once a user has Metamask installed and an Ethereum address, they can register, consume or stake on datasets on Ocean Market.

</details>

<details>

<summary>How is Ocean different from other data marketplaces?</summary>

Ocean Protocol is a decentralized data marketplace which gives users complete control of their data. The Ocean Protocol technology is built on smart contracts, decentralized computer scripts with no intermediary that are triggered by the users. The Ocean Market exposes the functionality of the smart contracts in a browser-friendly interface. Data providers and consumers can discover one another and transact in a peer-to-peer manner with the minimal amount of intermediary involvement.

</details>

<details>

<summary>How do I price my data?</summary>

Ocean gives you two different options for pricing your data - fixed price or free. You need to decide what your dataset is worth and how you want to price it. You can change the price but you can’t change the price format (e.g. from fixed to free).

</details>

<details>

<summary>Is my data secure?</summary>

Yes. Ocean Protocol understands that some data is too sensitive to be shared — potentially due to GDPR or other reasons. For these types of datasets, we offer a unique service called compute-to-data. This enables you to monetise the dataset that sits behind a firewall without ever revealing the raw data to the consumer. For example, researchers and data scientists pay to run their algorithms on the data set and the computation is performed behind a firewall; all the researchers or data scientists receive is the results generated by their algorithm.

</details>

<details>

<summary>Where is my data stored?</summary>

Ocean does not provide data storage. Users have the choice to store their data on their own servers, cloud or decentralized storage. Users need only to provide a URL to the dataset, which is then encrypted as a means to protect the access to the dataset.

</details>

<details>

<summary>How do I control who accesses my data?</summary>

Ocean provides tools for access control, fine grained permissions, passlisting and blocklisting addresses. Data and AI services can be shared under the conditions set by the owner of data. There is no central intermediary, which ensures no one can interfere with the transaction and both the publisher and user have transparency.

</details>

<details>

<summary>Can I restrict who is able to access my dataset?</summary>

Yes - Ocean has implemented fine grained permissions. This means that you can create allow and deny lists that restrict access from certain individuals or limit access to particular organizations.

</details>

<details>

<summary>What is the reach of Ocean Market - how many data buyers can I sell to?</summary>

Hundreds of unique datasets are available that are sourced from private individuals, research institutions, commercial enterprises and government. Publishing data on Ocean offers data providers and algorithm owners an exciting new channel to connect with a rapidly growing community of Web3 enthusiasts and data science professionals around the world.

</details>

### Technical Questions

<details>

<summary>Why does Ocean Protocol use the Blockchain?</summary>

For both providers and consumers of data, blockchain is a superior substrate for building applications.Blockchain allows business logic to be instantiated in a network and triggered by the users, without intermediaries. This innovation promises lower transaction costs, higher security, more control, less errors and more transparency & auditability.

</details>

<details>

<summary>The blockchain is public - does this mean that anyone can access my data?</summary>

No one is able to access data via the blockchain without purchasing access (with the datatoken) though the smart contract. Ocean smart contracts encrypt the URL to the dataset before it is published on the blockchain. This means that only the encrypted URL will be queryable in the public blockchain. Ocean technology facilitates data access to the consumer via a proxy (Ocean Provider) and the unencrypted url is never exposed.

</details>

<details>

<summary>What is a smart contract and why is it relevant?</summary>

The blockchain can do more than just store information - it can also run code. A smart contract is an executable script that runs on the blockchain, with no intermediary and is fully transparent and auditable by anyone. In Ocean, smart contracts facilitate access to data and AI if the access conditions set out by the publisher are fulfilled.

</details>

<details>

<summary>What is a datatoken?</summary>

A datatoken is an access token to datasets and services published in the Ocean ecosystem. Datatokens can be purchased via the Ocean Market or on a decentralized crypto exchange. . If a consumer wishes to access a dataset, they must acquire the datatoken and then exchange the datatoken for access to the dataset.

</details>

<details>

<summary>How do I acquire datatokens?</summary>

Datatokens can be acquired and traded in Ocean Market. There are several ways to acquire data tokens. Data publishers can acquire datatokens by publishing datasets and then receiving the generated datatokens.

Consumers can click "buy" on an asset in Ocean Market to buy and redeem a datatoken in exchange for access to a dataset.

Datatokens can also be sent from anyone who holds a datatoken for a particular asset.

</details>

### Data Selling Questions

<details>

<summary>How are organizations leveraging data sharing?</summary>

For the most part organizations are leveraging data sharing to benefit from data monetization, however increasingly organizations are also sharing data in order to boost their progress on sustainability goals. For example, data aggregated from vehicles can not only bring new revenue streams to automotive firms but can also be used to battle pollution.

</details>

<details>

<summary>Does it pay to become a marketplace operator?</summary>

Yes. Marketplace operators benefit from earning commission on marketplace transactions related to data consumption. Ocean Market is primarily focussed on monetising data however it is also designed to handle the sale of any digital asset or service. As a result the total addressable market goes way beyond revenues from just selling data. Operating costs for an Ocean-powered marketplace are moderate and the base code is open source and available free of charge under the Apache 2 license.

</details>

<details>

<summary>Why Publish?</summary>

Publishing data, algorithms and other digital assets and services on an Ocean-powered marketplace offers numerous opportunities to earn on the future revenue streams connected to that data as well as build lucrative ecosystem that add value to the published asset. It also allows for the discovery and insights into new use cases and applications of the published asset.

</details>

<details>

<summary>What about the price fluctuation of Ocean?</summary>

Price fluctuation is mitigated through the use of the Ocean backed stable coin H2O.

</details>

<details>

<summary>Who pays for gas fees?</summary>

Gas fees for marketplace transactions are paid by the user initiating the transaction (for publishing, consuming, etc).

</details>

<details>

<summary>Where do the docker containers run?</summary>

Dockers containers can run anywhere. Ocean Market use a docker run by the Ocean Protocol Foundation OPF); limit: 1 CPU limit / 60 seconds max. NOTE: This means OPF technically has access to data. In the case of a forked Ocean-powered marketplace the owner of marketplace must set up computation environment. If individual users of the marketplace are concerned with security they should be prepared to host both the data and provide compute-to-data services on premise.

</details>

<details>

<summary>Who pays for the computation?</summary>

The marketplace owner.

</details>

<details>

<summary>What cryptocurrency do I need for transactions?</summary>

The type if cryptocurrencies needed for transactions on the marketplace depends on which network(s) the marketplace is running (Ethereum, Polygon, EWT, BSC, Moonriver, etc.). Regardless of network, users will need to have Ocean tokens as well as the corresponding network token, which is used to pay for gas.

</details>

<details>

<summary>Can I use the off the shelf CSS available in the repo?</summary>

Marketplace name, logo and typeface must be changed by the client. Slight modification would be enough for compliance. For more information consult the READ ME file on GitHub. https://github.com/oceanprotocol/market#-forking

</details>

<details>

<summary>What’s to come with Ocean this year?</summary>

Checkout our [roadmap](https://oceanprotocol.com/technology/roadmap) to see what's we are currently working on. If you are interested in tracking our progress towards these goals then take a look at our [github](https://github.com/oceanprotocol/).

</details>

## Data Farming FAQ

<details>

<summary>What assets are eligible for Data Farming?</summary>

The data asset may be of any type — dataset (for static URIs), algorithm for Compute-to-Data, or any other Datatoken token-gated system. The data asset may be fixed price or free price. You can find more details in the [DF Background page](../rewards/df-background.md#assets-that-qualify-for-data-farming)

</details>

<details>

<summary>When exactly does counting start and finish, for a given week?</summary>

The counting starts at 12.01am on Thursday, and ends at 11.59pm on the following Wednesday.

</details>

<details>

<summary>I staked for just one day. What rewards might I expect?</summary>

At least 50 snapshots are randomly taken throughout the week. If you’ve staked just one day, and all else being equal, you should expect 1/7 the rewards compared to the full 7 days.

</details>

<details>

<summary>The datatoken price may change throughout the week. What price is taken in the DCV calculation?</summary>

The price is taken at the same time as each consume. E.g. if a data asset has three consumes, where price was 1 OCEAN when the first consume happened, and the price was 10 OCEAN when the other consumes happened, then the total DCV for the asset is 1 + 10 + 10 = 21.

</details>

<details>

<summary>Can the reward function change during a given week?</summary>

No. At the beginning of a new DF round (DF1, DF2, etc), rules are laid out, either implicitly if no change from previous round, or explicitly in a blog post if there are new rules. This is: reward function, bounds, etc. Then teams stake, buy data, consume, etc. And LPs are given DF rewards based on staking, DCV, etc at the end of the week. Overall cycle time is one week.

Caveat: it’s no at least in theory! Sometimes there may be tweaks if there is community consensus, or a bug.

</details>

## veOCEAN FAQ

<details>

<summary>What is the official formula for the Linear Decay?</summary>

The Linear Decay formula for veOCEAN can be expressed as follows in python.

```python
FOUR_YEARS = 60 * 60 * 24 * 7 * 52

veOcean_balance = OCEAN_amount_locked * (your_unlock_timestamp — current_unix_timestamp ) / FOUR_YEARS
```

To learn more about systems driving veOCEAN and Data Farming, please [visit our df-py github repository](https://github.com/oceanprotocol/df-py).

</details>

## Staking FAQs

<details>

<summary>What about passive stakers — people who just want to stake in one place and be done?</summary>

Earnings are passive by default

</details>

<details>

<summary>What about active stakers — people who want to do extra work and get rewarded?</summary>

Ot works. Half the DF revenue goes to veOCEAN stake that users can allocate. Allocate well → more $$

</details>

## Pricing FAQs

<details>

<summary>In this scheme, can people stake on fixed-price datasets?</summary>

Yes. They allocate their veOCEAN to datasets. Then DF rewards follow the usual DF formula: DCV \* veOCEAN stake.

</details>

<details>

<summary>In this scheme, can people stake on free datasets?</summary>

Yes. They allocate their veOCEAN to datasets. Then DF rewards follow the usual DF formula: DCV \* veOCEAN stake. Except in this case although DCV is 0, the gas fees will still count towards calculating rewards.

</details>

<details>

<summary>Does this work for other pricing schemes?</summary>

Yes, from the get-go! It doesn’t matter how data is priced, this works for all schemes.

</details>

## Chains FAQ

<details>

<summary>Which chain is veOCEAN be deployed on?</summary>

[veOCEAN & DF](https://github.com/oceanprotocol/contracts/tree/main/contracts/ve) core contracts are deployed on Ethereum mainnet and allow users to allocate veOCEAN tokens to any asset, on any chain.

</details>

<details>

<summary>Which networks are eligible for Data Farming?</summary>
Data assets for DF may published in any network where Ocean’s deployed in production: Eth Mainnet, Polygon, BSC, and more.

You can find a list of [all supported chains here](https://docs.oceanprotocol.com/discover/networks).

</details>

<details>

<summary>Where can I find the veOCEAN and DF contracts?</summary>

They are deployed on Ethereum mainnet, alongside other Ocean contract deployments. You can find the [full list of contracts here](https://github.com/oceanprotocol/contracts/blob/main/addresses/address.json).

</details>

<details>

<summary>What is the official veOCEAN epoch start_time?</summary>

veFeeDistributor has a start_time of 1663804800 (Thu Sep 22 2022 00:00:00)

</details>

<details>

<summary>Will the Market still need to be multi-chain?</summary>

Yes, Ocean Market still needs to be multi-chain: all the reasons that we went multi-chain for are as valid as ever.

</details>

<details>

<summary>Which chain supports Fixed Price Assets?</summary>

You can publish Fixed Price Assets to any chain that Ocean supports.

</details>