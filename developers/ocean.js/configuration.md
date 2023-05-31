# Configuration

### Obtaining API key for Ethereum node provider

Ocean Protocol's smart contracts are deployed on EVM-compatible networks. Using an API key provided by a third-party Ethereum node provider allows you to interact with the Ocean Protocol's smart contracts on the supported networks without requiring you to host a local node.

Choose any API provider of your choice. Some of the commonly used are:

* [Infura](https://infura.io/)
* [Alchemy](https://www.alchemy.com/)
* [Moralis](https://moralis.io/)

The supported networks are listed [here](../../discover/networks/).

### Create a directory

Let's start with creating a working directory where we store the environment variable file, configuration files and the scripts.

```
mkdir my-ocean-project
cd my-ocean-project
```

### Create a `.env` file

In the working directory create a `.env` file. The content of this file will store the values for following variables:

| Variable name           | Description                                                                                                                                                                 | Required |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- |
| **OCEAN\_NETWORK**      | Name of the network where the Ocean Protocol's smart contracts are deployed.                                                                                                | Yes      |
| **OCEAN\_NETWORK\_URL** | The URL of the Ethereum node (along with API key for non-local networks)\*\*                                                                                                | Yes      |
| **PRIVATE\_KEY**        | The private key of the account which you want to use. A private key is made up of 64 hex characters. Make sure you have sufficient balance to pay for the transaction fees. | Yes      |
| **AQUARIUS\_URL**       | The URL of the Aquarius. This value is needed when reading an asset from off-chain store.                                                                                   | No       |
| **PROVIDER\_URL**       | The URL of the Provider. This value is needed when publishing a new asset or update an existing asset.                                                                      | No       |

{% hint style="info" %}
Treat this file as a secret and do not commit this file to git or share the content publicly. If you are using git, then include this file name in `.gitignore` file.
{% endhint %}

The below tabs show partially filled `.env` file content for some of the supported networks.

{% tabs %}
{% tab title="Mainnet" %}
{% code title=".env" %}
```
# Mandatory environment variables

OCEAN_NETWORK=mainnet
OCEAN_NETWORK_URL=<replace this>
PRIVATE_KEY=<secret>

# Optional environment variables

AQUARIUS_URL=https://v4.aquarius.oceanprotocol.com/
PROVIDER_URL=https://v4.provider.oceanprotocol.com
```
{% endcode %}
{% endtab %}

{% tab title="Polygon" %}
{% code title=".env" %}
```
# Mandatory environment variables

OCEAN_NETWORK=polygon
OCEAN_NETWORK_URL=<replace this>
PRIVATE_KEY=<secret>

# Optional environment variables

AQUARIUS_URL=https://v4.aquarius.oceanprotocol.com/
PROVIDER_URL=https://v4.provider.oceanprotocol.com
```
{% endcode %}
{% endtab %}

{% tab title="Local (using Barge)" %}
{% code title=".env" %}
```
# Mandatory environment variables
OCEAN_NETWORK=development
OCEAN_NETWORK_URL=http://172.15.0.3:8545/
AQUARIUS_URL=http://172.15.0.5:5000
PROVIDER_URL=http://172.15.0.4:8030

# Replace PRIVATE_KEY if needed
PRIVATE_KEY=0xc594c6e5def4bab63ac29eed19a134c130388f74f019bc74b8f4389df2837a58
```
{% endcode %}
{% endtab %}
{% endtabs %}

Replace `<replace this>` with the appropriate values. \*\*You can see all the networks configuration on Oceanjs' [config helper](https://github.com/oceanprotocol/ocean.js/blob/main/src/config/ConfigHelper.ts#L42).

### Setup dependencies

In this step all required dependencies will be installed.

### Installation & Usage

Let's install Oceanjs library into your current project by running:

{% tabs %}
{% tab title="Terminal" %}
```bash
npm init
npm i @oceanprotocol/lib@3.0.0-next.5 dotenv crypto-js ethers@5.7.4 @truffle/hdwallet-provider
```
{% endtab %}
{% endtabs %}

### Create a configuration file

A configuration file will read the content of the `.env` file and initialize the required configuration objects which will be used in the further tutorials. The below scripts creates a Web3 wallet instance and an Ocean's configuration object.

Create the configuration file in the working directory i.e. at the same path where the `.env` is located.

{% tabs %}
{% tab title="config.js" %}
{% code title="config.js" %}
```javascript
require('dotenv').config();
const { Aquarius, ZERO_ADDRESS, ConfigHelper, configHelperNetworks } = require('@oceanprotocol/lib');
const { providers } = require('ethers')
const ethers = require('ethers');
async function oceanConfig(){

  // Get configuration for the given network
  const provider = new providers.JsonRpcProvider(
    process.env.OCEAN_NETWORK_URL || configHelperNetworks[1].nodeUri
  )

  const ethersProvider = new ethers.Wallet(
    process.env.PRIVATE_KEY,
    provider
  );

  const publisherAccount = await ethersProvider.provider.getSigner(ethersProvider.address);
  const consumerAccount = publisherAccount
  const stakerAccount = publisherAccount

  let oceanConfig = new ConfigHelper().getConfig(
    parseInt(String((await provider.getSigner(0).provider.getNetwork()).chainId))
  )
  const aquarius = new Aquarius(oceanConfig?.metadataCacheUri)

  // If using local development environment, read the addresses from local file.
  // The local deployment address file can be generated using barge.
  if (process.env.OCEAN_NETWORK === 'development') {
    const addresses = JSON.parse(
      // eslint-disable-next-line security/detect-non-literal-fs-filename
      fs.readFileSync(
        process.env.ADDRESS_FILE ||
          `${homedir}/.ocean/ocean-contracts/artifacts/address.json`,
        'utf8'
      )
    ).development

    oceanConfig = {
      ...oceanConfig,
      oceanTokenAddress: addresses.Ocean,
      poolTemplateAddress: addresses.poolTemplate,
      fixedRateExchangeAddress: addresses.FixedPrice,
      dispenserAddress: addresses.Dispenser,
      nftFactoryAddress: addresses.ERC721Factory,
      sideStakingAddress: addresses.Staking,
      opfCommunityFeeCollector: addresses.OPFCommunityFeeCollector
    };
  }

  oceanConfig = {
    ...oceanConfig,
    publisherAccount: publisherAccount,
    consumerAccount: consumerAccount,
    stakerAccount: stakerAccount,
    aquarius: aquarius,
    ethersProvider: ethersProvider,
  };

  return oceanConfig
};

module.exports = {
  oceanConfig
}
```
{% endcode %}
{% endtab %}
{% endtabs %}

Now you have set up the necessary files and configurations to interact with Ocean Protocol's smart contracts using ocean.js. You can proceed with further tutorials or development using these configurations.