---
description: >-
  This page shows how you can publish a data NFT, a datatoken & a data asset all
  in once in different scenarios.
---

# Publish flow

[**ocean.py**](https://github.com/oceanprotocol/ocean.py) is a [Python library](https://pypi.org/project/ocean-lib/) to privately & securely publish, exchange, and consume data, using [Ocean Protocol](https://www.oceanprotocol.com/).

In this page, we provide some tips & tricks for publishing an asset on Ocean Market using ocean.py.

We assume you've already (a) [installed Ocean](https://github.com/oceanprotocol/ocean.py/blob/main/READMEs/install.md), and (b) done [local setup](https://github.com/oceanprotocol/ocean.py/blob/main/READMEs/setup-local.md) or [remote setup](https://github.com/oceanprotocol/ocean.py/blob/main/READMEs/setup-remote.md). This flow works for either one, without any changes between them.

In the Python console:

```python
#data info
name = "Branin dataset"
url = "https://raw.githubusercontent.com/trentmc/branin/main/branin.arff"

#create data asset
(data_nft, datatoken, ddo) = ocean.assets.create_url_asset(name, url, {"from": alice})

#print
print("Just published asset:")
print(f"  data_nft: symbol={data_nft.symbol()}, address={data_nft.address}")
print(f"  datatoken: symbol={datatoken.symbol()}, address={datatoken.address}")
print(f"  did={ddo.did}")
```

You've now published an Ocean asset!

* `data_nft` is the base (base IP)
* `datatoken` for access by others (licensing)
* `ddo` holding metadata

<figure><img src="../../.gitbook/assets/200.webp" alt=""><figcaption></figcaption></figure>

### Appendix

For more information regarding: Data NFT & Datatokens interfaces and how they are implemented in Solidity, we suggest to follow up this [article](../datanft-and-datatoken/) and [contracts repo](https://github.com/oceanprotocol/contracts) from GitHub.

As you may want to explore more the DDO specs,  structure & meaning, we invite you to consult [DDO Specification](../ddo-specification.md) section.

#### Publishing Alternatives

Here's an example similar to the `create()` step above, but exposes more fine-grained control.

In the same python console:

```python
# Specify metadata and services, using the Branin test dataset
date_created = "2021-12-28T10:55:11Z"
metadata = {
    "created": date_created,
    "updated": date_created,
    "description": "Branin dataset",
    "name": "Branin dataset",
    "type": "dataset",
    "author": "Trent",
    "license": "CC0: PublicDomain",
}

# Use "UrlFile" asset type. (There are other options)
from ocean_lib.structures.file_objects import UrlFile
url_file = UrlFile(
    url="https://raw.githubusercontent.com/trentmc/branin/main/branin.arff"
)

# Publish data asset
from ocean_lib.models.datatoken_base import DatatokenArguments
_, _, ddo = ocean.assets.create(
    metadata,
    {"from": alice},
    datatoken_args=[DatatokenArguments(files=[url_file])],
)
```

#### DDO Encryption or Compression

The DDO is stored on-chain. It's encrypted and compressed by default. Therefore it supports GDPR "right-to-be-forgotten" compliance rules by default.

You can control this during `create()`:

* To disable encryption, use `ocean.assets.create(..., encrypt_flag=False)`.
* To disable compression, use `ocean.assets.create(..., compress_flag=False)`.
* To disable both, use `ocean.assetspy.create(..., encrypt_flag=False, compress_flag=False)`.

#### Create _just_ a data NFT

Calling `create()` like above generates a data NFT, a datatoken for that NFT, and a ddo. This is the most common case. However, sometimes you may want _just_ the data NFT, e.g. if using a data NFT as a simple key-value store. Here's how:

```python
data_nft = ocean.data_nft_factory.create({"from": alice}, 'NFT1', 'NFT1')
```

If you call `create()` after this, you can pass in an argument `data_nft_address:string` and it will use that NFT rather than creating a new one.

#### Create a datatoken from a data NFT

Calling `create()` like above generates a data NFT, a datatoken for that NFT, and a ddo object. However, we may want a second datatoken. Or, we may have started with _just_ the data NFT, and want to add a datatoken to it. Here's how:

```python
datatoken = data_nft.create_datatoken({"from": alice}, "Datatoken 1", "DT1")
```

If you call `create()` after this, you can pass in an argument `deployed_datatokens:List[Datatoken1]` and it will use those datatokens during creation.

#### Create an asset & pricing schema simultaneously

Ocean Assets allows you to bundle several common scenarios as a single transaction, thus lowering gas fees.

Any of the `ocean.assets.create_<type>_asset()` functions can also take an optional parameter that describes a bundled pricing schema (Dispenser or Fixed Rate Exchange).&#x20;

Here is an example involving an exchange:

{% code overflow="wrap" %}
```python
from ocean_lib.models.fixed_rate_exchange import ExchangeArguments
(data_nft, datatoken, ddo) = ocean.assets.create_url_asset(
    name,
    url,
    {"from": alice},
    pricing_schema_args=ExchangeArguments(rate=to_wei(3), base_token_addr=ocean.OCEAN_address, dt_decimals=18)
)

assert len(datatoken.get_exchanges()) == 1
```
{% endcode %}
