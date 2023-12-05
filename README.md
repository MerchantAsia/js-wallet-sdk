# js-wallet-sdk

This is a typescript/javascript language wallet solution that supports offline transactions. We currently support various mainstream public
blockchains, and will gradually release the source codes for each blockchain.

## Npm Install
To obtain the latest version, simply require the project using npm:

```shell
# needed for all coins
npm install @okxweb3/crypto-lib
npm install @okxweb3/coin-base

# for eth
npm install @okxweb3/coin-ethereum

# for bitcoin
npm install @okxweb3/coin-bitcoin
```

## Build Locally
You can build the sdk locally ,and run test-code.
```shell
sh build.sh
```

## Supported chains

|          | Account Generation | Transaction Creation | Transaction Signing |
|----------|-------------------|----------------------|---------------------|
| BTC      | ✅                 | ✅                    | ✅                   | 
| Ethereum | ✅                 | ✅                    | ✅                   |
| Aptos    | ✅                 | ✅                    | ✅                   |
| Cosmos   | ✅                 | ✅                    | ✅                   |
| Eos      | ✅                 | ✅                    | ✅                   |
| Flow     | ✅                 | ✅                    | ✅                   |
| Stacks   | ✅                 | ✅                    | ✅                   |
| Starknet | ✅                 | ✅                    | ✅                   |
| Sui      | ✅                 | ✅                    | ✅                   |
| Tron     | ✅                 | ✅                    | ✅                   |
| Osmosis  | ✅                 | ✅                    | ✅                   |
| Cardano  | ✅                 | ✅                    | ✅                   |


*BTC: Supports Supports BRC20-related functions, including inscription creation, BRC20 buying and selling.

## Main modules

- crypto-lib: Handles general security and signature algorithms.
- coin-base: Provides  coin common interface.
- coin-*: Implements transaction creation and signature in each coin type.


## Example

For specific usage examples of each coin type, please refer to the corresponding test files. Remember to replace the
placeholder private key with your own private key, which is generally in hex format.

## Feedback

You can provide feedback directly in GitHub Issues, and we will respond promptly.

## License
Most packages or folders are MIT licensed, see package or folder for the respective license.


sign drc 20
```typescript
import { DogeWallet } from "@okxweb3/coin-bitcoin";
let wallet = new DogeWallet()
        let privateKey = ""

        const commitTxPrevOutputList: PrevOutput[] = [];
        commitTxPrevOutputList.push({
            txId: "3cb1d8da082b2146b8f4c09b06e38eb37f0263ecefb8a52600accc75ccef4c90",
            vOut: 1,
            amount: 793850000,
            address: "DJu5mMUKprfnyBhot2fqCsW9sZCsfdfcrZ",
            privateKey: privateKey,
        });
        const inscriptionDataList: DrcInscriptionData[] = [];
        inscriptionDataList.push({
            contentType: "text/plain;charset=utf-8",
            body: `{"p":"drc-20","op":"mint","tick":"MARS","amt":"210000000000"}`,
            revealAddr: "DFuDR3Vn22KMnrnVCxh6YavMAJP8TCPeA2",
            repeat: 2,
        });

        const request = {
            commitTxPrevOutputList,
            commitFeeRate: 50000,
            revealFeeRate: 50000,
            inscriptionDataList,
            changeAddress: "DFuDR3Vn22KMnrnVCxh6YavMAJP8TCPeA2",
        };
        let res= await wallet.signTransaction({privateKey:privateKey,data:{type:1,data:request}})
        console.log(JSON.stringify(res))
