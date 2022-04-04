# Balancer SDK

A JavaScript SDK which provides commonly used utilties for interacting with Balancer Protocol V2.

###### tags: `Balancer`

Fork [balancer-sdk/balancer-js](https://github.com/balancer-labs/balancer-sdk/tree/develop/balancer-js)

## 1. Modification

### 1.1. Modify .env.development

Modify BALANCER_SUBGRAPH_URL

### 1.2. Modify src/constants/contracts.ts

Add Fuji Testnet config

```config=
[Network.FUJI]: {
        chainId: Network.FUJI, //43113
        vault: '0xF20D313685665bf745B720FE81b927fAFcfB18A2',
        weth: '0xbAD9016aa18Cf22d08aefd3B86c0D36E8C222B83',
        multicall: '0xC471AFa18cD037a9bb032bE72651Fe3Eaa466eBA',
        subgraphUrl:
            'subgraph-url-here',
    },
```

Add Avalanche Mainnet config

```config=
[Network.AVALANCHE]: {
        chainId: Network.AVALANCHE, //43114
        vault: 'todo vault adress here',
        weth: '0xB31f66AA3C1e785363F0875A1B74E27b85FD66c7',
        multicall: 'todo multicall address here',
        subgraphUrl:
            'subgraph-url-here',
    }
```

### 1.3. Modify src/constants/network.ts

Modify Network, add

```typescript=
FUJI = 43113,
AVALANCHE = 43114
```

### 1.4. Mofify src/sor/token-price/coingeckoTokenPriceService.ts

Modify platform(), add

```typescript=
case 43113:
    return "ethereum";
case 43114:
    return "avalanche";
```

Modify nativeAssetId(), add

```typescript=
case 43113:
    return "eth";
case 43114:
    return "avax";
```

### 1.5. Modify src/subgraph/codegen.yml

Modify schema, use correct schema.

## 2. Build balancer-sdk

### 2.1. Clone and install dependencies

```bash=
git clone this-project-code
```

Install dependencies
```bash=
yarn
```

### 2.1. Balancer Subgraph Queries

Anytime a new query is added, run `yarn generate` to regenerate the client files, fully typed.

```bash=
yarn generate
```

### 2.2. Build the project

```bash=
yarn build
```





