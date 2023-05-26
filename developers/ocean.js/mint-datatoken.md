# Mint Datatokens

This tutorial guides you through the process of minting datatokens and sending them to a receiver address. The tutorial assumes that you already have the address of the datatoken contract which is owned by you.

#### Prerequisites

* [Obtain an API key](broken-reference)
* [Set up the .env file](broken-reference)
* [Install the dependencies](broken-reference)
* [Create a configuration file](configuration.md)

#### Create a script to mint datatokens

Create a new file in the same working directory where configuration file (`config.js`) and `.env` files are present, and copy the code as listed below.

{% tabs %}
{% tab title="mint_datatoken.js" %}
{% code title="mint_datatoken.js" %}
```javascript
// Note: Make sure .env file and config.js are created and setup correctly
const { oceanConfig } = require('./config.js');
const { amountToUnits } = require ('@oceanprotocol/lib');
const ethers = require('ethers');

// Define a function createFRE()
const createMINT = async () => {

    let config = await oceanConfig();
    const publisher = config.publisherAccount
    const publisherAccount = await config.publisherAccount.getAddress()

    const minAbi = [
        {
        constant: false,
        inputs: [
            { name: 'to', type: 'address' },
            { name: 'value', type: 'uint256' }
        ],
        name: 'mint',
        outputs: [{ name: '', type: 'bool' }],
        payable: false,
        stateMutability: 'nonpayable',
        type: 'function'
        }
    ]

    const tokenContract = new ethers.Contract(config.oceanTokenAddress, minAbi, publisher)
    const estGasPublisher = await tokenContract.estimateGas.mint(
        publisherAccount,
        amountToUnits(null, null, '1000', 18)
    )
    const trxReceipt = await sendTx(
        estGasPublisher,
        publisher,
        1,
        tokenContract.mint,
        publisherAccount,
        amountToUnits(null, null, '1000', 18)
    )
    
    return {
        trxReceipt
    };
};

// Call the createFRE() function 
createMINT()
  .then(({ trxReceipt }) => {
    console.log(`TX Receipt ${trxReceipt}`);
    process.exit(1);
  })
  .catch((err) => {
    console.error(err);
    process.exit(1);
  });
```
{% endcode %}

**Execute script**

```
node mint_datatoken.js
```
{% endtab %}
{% endtabs %}