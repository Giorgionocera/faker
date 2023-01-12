# Page 1

{% tabs %}
{% tab title="Gitpod" %}
```
secretcli tx compute store ./contract.wasm --gas 5000000 --from a -y
```
{% endtab %}

{% tab title="Secret IDE" %}
To interact with the blockchain, we first need to initialize a wallet. Use the included "New Wallet" command from the GUI, or from the terminal run

`secretcli keys add <name>` (replace \<name> with your wallet name)

After adding this key, note the _address_ of the wallet. The address starts with the prefix `secret1...`

Now, we can request funds to the wallet, so it has enough currency to send transactions.

Visit [https://faucet.pulsar.scrttestnet.com/](https://faucet.pulsar.scrttestnet.com/) and paste your wallet address to receive testnet tokens

Finally, we can deploy our contract -

```
secretcli tx compute store ./contract.wasm --gas 5000000 --from <name> --chain-id pulsar-2
```
{% endtab %}

{% tab title="Docker LocalSecret" %}
To interact with the blockchain, we first need to initialize a wallet

`secretcli keys add <name>` (replace \<name> with your wallet name)

After adding this key, note the _address_ of the wallet. The address starts with the prefix `secret1...`

Now, we can request funds to the wallet, so it has enough currency to send transactions. For that we use the LocalSecret's built-in faucet

```
curl http://localhost:5000/faucet?address=<wallet_address>
secretcli tx compute store ./contract.wasm --gas 5000000 --from <name> --chain-id secretdev-1
```
{% endtab %}

{% tab title="Public Testnet" %}
To use the public testnet (codenamed pulsar-2), we need to configure SecretCLI to talk to it.

Use the following commands to configure SecretCLI

```
secretcli config node https://rpc.pulsar.scrttestnet.com
secretcli config output json
secretcli config chain-id pulsar-2
secretcli config keyring-backend test
```

To interact with the blockchain, we first need to initialize a wallet

`secretcli keys add <name>` (replace \<name> with your wallet name)

After adding this key, note the _address_ of the wallet. The address starts with the prefix `secret1...`

Now, we can request funds to the wallet, so it has enough currency to send transactions. For that we use the faucet from the public testnet:

{% embed url="https://faucet.pulsar.scrttestnet.com/" %}

Once the tokens have been delivered, we can now **store** the contract code on chain

```
secretcli tx compute store ./contract.wasm --gas 5000000 --from <name>
```
{% endtab %}
{% endtabs %}

